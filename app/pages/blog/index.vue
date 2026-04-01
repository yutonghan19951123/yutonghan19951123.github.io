<script setup lang="ts">
  const { data: page } = await useAsyncData('blog-page', () => {
    return queryCollection('pages').path('/blog').first()
  })
  if (!page.value) {
    throw createError({
      statusCode: 404,
      statusMessage: 'Page not found',
      fatal: true
    })
  }
  const { data: posts } = await useAsyncData('blogs', () =>
    queryCollection('blog').order('date', 'DESC').all()
  )
  if (!posts.value) {
    throw createError({
      statusCode: 404,
      statusMessage: 'blogs posts not found',
      fatal: true
    })
  }

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
        <div class="mx-auto max-w-2xl lg:mx-0">
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
              <UButton v-bind="page.links[0]" />
            </div>
          </div>
        </div>
      </div>
    </div>

    <section class="pb-16 sm:pb-24">
      <div class="mx-auto max-w-7xl px-6 lg:px-8">
        <div class="!pt-0">
          <Motion
            v-for="(post, index) in posts"
            :key="index"
            :initial="{ opacity: 0, transform: 'translateY(10px)' }"
            :while-in-view="{ opacity: 1, transform: 'translateY(0)' }"
            :transition="{ delay: 0.2 * index }"
            :in-view-options="{ once: true }"
          >
            <div class="group mb-16 pb-16 last:mb-0">
              <div class="grid grid-cols-1 md:grid-cols-2 gap-8 items-center">
                <div class="order-1">
                  <img
                    :src="post.image"
                    :alt="post.title"
                    class="object-cover w-full h-56 rounded-lg shadow-lg group-hover:scale-105 transition-transform duration-300 border-6 border-gray-200 dark:border-gray-700"
                    :class="
                      index % 3 === 0
                        ? '-rotate-2'
                        : index % 3 === 1
                          ? 'rotate-1'
                          : 'rotate-2'
                    "
                  />
                </div>
                <div class="order-2">
                  <div class="flex items-center gap-2 mb-2">
                    <span class="text-sm text-muted">
                      {{
                        new Date(post.date).toLocaleDateString('en-US', {
                          year: 'numeric',
                          month: 'long'
                        })
                      }}
                    </span>
                  </div>
                  <h2
                    class="text-base font-semibold text-gray-900 dark:text-white mb-2"
                  >
                    {{ post.title }}
                  </h2>
                  <p class="text-gray-500 dark:text-gray-300 mb-4 text-sm">
                    {{ post.description }}
                  </p>
                  <ULink
                    :to="post.path"
                    class="text-sm text-primary flex items-center"
                  >
                    Read Article
                    <UIcon
                      name="i-lucide-arrow-right"
                      class="size-4 text-primary transition-all opacity-0 group-hover:translate-x-1 group-hover:opacity-100"
                    />
                  </ULink>
                </div>
              </div>
            </div>
          </Motion>
        </div>
      </div>
    </section>
  </div>
</template>
