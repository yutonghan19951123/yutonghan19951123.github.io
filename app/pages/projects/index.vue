<script setup lang="ts">
  import dayjs from 'dayjs'

  const { data: page } = await useAsyncData('projects-page', () => {
    return queryCollection('pages').path('/projects').first()
  })
  if (!page.value) {
    throw createError({
      statusCode: 404,
      statusMessage: 'Page not found',
      fatal: true
    })
  }

  const { data: projects } = await useAsyncData('projects', async () => {
    const all = await queryCollection('projects').all()
    return all.sort((a, b) => {
      const dateA = dayjs(a.date)
      const dateB = dayjs(b.date)
      return dateB.valueOf() - dateA.valueOf()
    })
  })

  const { global } = useAppConfig()

  useSeoMeta({
    title: page.value?.seo?.title || page.value?.title,
    ogTitle: page.value?.seo?.title || page.value?.title,
    description: page.value?.seo?.description || page.value?.description,
    ogDescription: page.value?.seo?.description || page.value?.description
  })
</script>

<template>
  <div v-if="page" class="min-h-screen">
    <div class="relative py-16 sm:py-24">
      <div class="mx-auto max-w-7xl px-6 lg:px-8">
        <div class="mx-auto max-w-xl lg:mx-0">
          <h1
            class="text-3xl font-bold tracking-tight text-gray-900 sm:text-5xl dark:text-gray-100"
          >
            {{ page.title }}
          </h1>
          <p class="mt-6 text-base leading-8 text-gray-500 dark:text-gray-400">
            {{ page.description }}
          </p>
          <div class="mt-6 flex items-center gap-x-6">
            <div v-if="page.links" class="flex items-center gap-2">
              <UButton
                :label="page.links[0]?.label"
                :to="global.meetingLink"
                v-bind="page.links[0]"
              />
              <UButton :to="`mailto:${global.email}`" v-bind="page.links[1]" />
            </div>
          </div>
        </div>
      </div>
    </div>

    <section class="pb-16 sm:pb-24">
      <div class="mx-auto max-w-7xl px-6 lg:px-8">
        <div class="!pt-0">
          <Motion
            v-for="(project, index) in projects"
            :key="project.title"
            :initial="{ opacity: 0, transform: 'translateY(10px)' }"
            :while-in-view="{ opacity: 1, transform: 'translateY(0)' }"
            :transition="{ delay: 0.2 * index }"
            :in-view-options="{ once: true }"
          >
            <div class="group mb-16 pb-16 last:mb-0">
              <div class="grid grid-cols-1 lg:grid-cols-2 gap-8 items-center">
                <div
                  class="order-2 lg:order-2"
                  :class="{ 'lg:order-1': index % 2 === 0 }"
                >
                  <div class="flex items-center gap-2 mb-2">
                    <span class="text-sm text-muted">
                      {{ dayjs(project.date).format('YYYY') }}
                    </span>
                  </div>
                  <h2
                    class="text-base font-semibold text-gray-900 dark:text-white mb-2"
                  >
                    {{ project.title }}
                  </h2>
                  <div class="text-gray-500 dark:text-gray-300 mb-4 text-sm">
                    {{ project.description }}
                  </div>
                  <ULink
                    :to="project.url"
                    class="text-sm text-primary flex items-center"
                  >
                    View Project
                    <UIcon
                      name="i-lucide-arrow-right"
                      class="size-4 text-primary transition-all opacity-0 group-hover:translate-x-1 group-hover:opacity-100"
                    />
                  </ULink>
                </div>
                <div
                  class="order-1 lg:order-1"
                  :class="{ 'lg:order-2': index % 2 === 0 }"
                >
                  <img
                    :src="project.image"
                    :alt="project.title"
                    class="object-cover w-full h-48 rounded-lg shadow-lg"
                  />
                </div>
              </div>
            </div>
          </Motion>
        </div>
      </div>
    </section>
  </div>
</template>
