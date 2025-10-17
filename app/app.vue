<script setup lang="ts">
  const colorMode = useColorMode()

  const color = computed(() =>
    colorMode.value === 'dark' ? '#020618' : 'white'
  )

  useHead({
    meta: [
      { charset: 'utf-8' },
      { name: 'viewport', content: 'width=device-width, initial-scale=1' },
      { key: 'theme-color', name: 'theme-color', content: color }
    ],
    link: [{ rel: 'icon', href: '/logo.png' }],
    htmlAttrs: {
      lang: 'en'
    }
  })

  useSeoMeta({
    titleTemplate: '%s - Nuxt Portfolio Template',
    ogImage:
      'https://assets.hub.nuxt.com/eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ1cmwiOiJodHRwczovL3BvcnRmb2xpby10ZW1wbGF0ZS5udXh0LmRldiIsImlhdCI6MTc0NTkzNDczMX0.XDWnQoyVy3XVtKQD6PLQ8RFUwr4yr1QnVwPxRrjCrro.jpg?theme=light',
    twitterImage:
      'https://assets.hub.nuxt.com/eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ1cmwiOiJodHRwczovL3BvcnRmb2xpby10ZW1wbGF0ZS5udXh0LmRldiIsImlhdCI6MTc0NTkzNDczMX0.XDWnQoyVy3XVtKQD6PLQ8RFUwr4yr1QnVwPxRrjCrro.jpg?theme=light',
    twitterCard: 'summary_large_image'
  })
</script>

<template>
  <UApp>
    <NuxtLayout>
      <div class="relative min-h-screen">
        <NuxtPage />
      </div>
    </NuxtLayout>
  </UApp>
</template>
