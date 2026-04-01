<script setup lang="ts">
  useSeoMeta({
    title: 'PhD Application Portfolio - Yutong Han',
    ogTitle: 'PhD Application Portfolio - Yutong Han',
    description:
      'Visualizing Complexity: From Evidence to Trust - Exploring the intersection of Human-AI Collaboration, Visual Epistemology, and Civic Media',
    ogDescription:
      'Visualizing Complexity: From Evidence to Trust - Exploring the intersection of Human-AI Collaboration, Visual Epistemology, and Civic Media'
  })

  const openPDF = (path: string) => {
    window.open(path, '_blank')
  }

  // Video URLs - Update these after uploading videos to external storage
  // Options: GitHub Releases, Cloudinary, or other CDN
  const videoUrls = {
    'ai-agent': '/img/projects/ai-agent/demo.mp4', // TODO: Replace with external URL
    '3d-pillar': '/img/projects/3d_pillar/demo.mp4', // TODO: Replace with external URL
    'dop-workspace': '/img/projects/dop/workspace.mp4' // This one might be OK if < 50MB
  }

  // Accordion state - default open Project 1
  const openItems = ref<Record<string, boolean>>({
    intersection: true,
    geospatial: false,
    pillars: false,
    'winter-olympic': false,
    wastewater: false
  })

  const toggleItem = (key: string) => {
    openItems.value[key] = !openItems.value[key]
  }

  // Projects data - simplified content
  const projects = [
    {
      key: 'intersection',
      label: 'Project 1: Intersection AI Agent Interface',
      subtitle:
        'A Visual-First Human-in-the-Loop System for Adaptive Traffic Signal Control',
      content: {
        overview:
          'A visual-first human-in-the-loop system that bridges the trust gap by overlaying semantic ground truth onto CCTV feeds via a custom Canvas engine. Combines visual auditability with LLM-driven natural language steering to transform opaque signal optimization into a transparent, collaborative process.',
        innovation: [
          'Dynamic Object Tracking: Real-time bounding boxes and tracking IDs',
          'Zone-Level Saturation Visualization: Sequential saturation logic via AOI polygons',
          'Confidence Exposure: Model confidence scores for real-time assessment'
        ],
        demo: {
          type: 'video',
          src: videoUrls['ai-agent'],
          link: '/blog/2025-10-30-ai-agent',
          linkText: 'View Project Details'
        }
      }
    },
    {
      key: 'geospatial',
      label: 'Project 2: Auto-Visualization for Geospatial Workflows',
      subtitle:
        'A Decoupled, Declarative Infrastructure for Instant Visual Analytics',
      content: {
        overview:
          'A decoupled, declarative infrastructure that automates the "last mile" of geospatial workflows. Type-driven inference engine generates optimal visual encodings by inspecting data schema on the fly, enabling instant visual analytics without manual configuration.',
        innovation: [
          'Type-Driven Inference: Automatic encoding generation from data schema',
          'Spatial Indexing: Dynamic viewport limiting, reducing data transmission by 80%+',
          'Composable Layers: Stack distinct datasets and dynamically switch rendering modes',
          'Performance Optimization: 60 FPS with city-scale datasets via incremental loading and debounced interactions'
        ],
        demo: {
          type: 'video',
          src: videoUrls['dop-workspace'],
          link: '/blog/2025-2-2-data-operation-platform-workspace',
          linkText: 'View Project Details'
        }
      }
    },
    {
      key: 'pillars',
      label: 'Project 3: "Pillars" - A 3D Interactive Framework',
      subtitle: 'A 3D Visualization Framework for Spatially Coincident Geodata',
      content: {
        overview:
          'A 3D visualization framework developed through problem-driven design study. Utilizes vertical extrusion and hybrid rendering to disentangle spatially coincident geodata, solving the "spaghetti effect" in OD analysis. Achieves real-time performance for 400,000+ daily trip records.',
        innovation: [
          'Hybrid Rendering: MapLibre (static topology) + deck.gl (dynamic flow)',
          'Declarative Middleware: Synchronizes UI and GPU state without manual DOM manipulation',
          'Performance: Optimized texture atlas and WebGL instancing for stable 60 FPS'
        ],
        demo: {
          type: 'video',
          src: videoUrls['3d-pillar'],
          link: '/blog/2025-12-1-3d-pillar',
          linkText: 'View Project Details'
        }
      }
    },
    {
      key: 'winter-olympic',
      label: 'Project 4: Which Winter Olympic Sport Fits You?',
      subtitle: 'Gamifying Data Journalism for Public Engagement',
      content: {
        overview:
          'A data journalism project that gamifies winter sports engagement through personality-driven interactive narratives. Self-taught character animation (After Effects) to create immersive motion graphics, transforming athletic data into engaging visual stories.',
        innovation: [
          'Character Animation: Self-directed learning in rigging and motion cycles',
          'Interactive Narrative: Psychological matching with data-driven infographics',
          'Public Engagement: Micro-encyclopedia format making niche sports accessible'
        ],
        demo: {
          type: 'gif',
          src: '/img/winter_olympic.gif',
          link: '/blog/2022-2-1-what-snow-sport-suit',
          linkText: 'View Project Details'
        }
      }
    },
    {
      key: 'wastewater',
      label: 'Project 5: Where Did Your Daily Wastewater Go?',
      subtitle: 'Explaining Environmental Impact via 3D Simulation',
      content: {
        overview:
          "Scientific visualization project investigating Miami-Dade County's wastewater journey and its ecological impact. Synthesized environmental reports and engineering blueprints to create high-fidelity 3D models (Autodesk Maya) translating complex technical information into accessible public narratives.",
        innovation: [
          '3D Modeling: High-fidelity facility models (clarifiers, treatment processes)',
          'Scientific Synthesis: Combined multiple data sources into coherent narratives',
          'Public Communication: Accessible visual storytelling for environmental issues'
        ],
        demo: {
          type: 'pdf',
          src: '/file/3d.pdf',
          linkText: 'View PDF Document'
        }
      }
    }
  ]

  // Sticky header tracking
  const activeStickyKey = ref<string | null>(null)
  const projectRefs = ref<Record<string, HTMLElement>>({})
  const projectHeaders = ref<Record<string, HTMLElement>>({})

  onMounted(() => {
    const updateActiveSticky = () => {
      const scrollTop = window.scrollY
      const headerOffset = 80 // Offset for sticky positioning

      // Find which project content is currently in view
      Object.keys(projectRefs.value).forEach(key => {
        const contentEl = projectRefs.value[key]
        const headerEl = projectHeaders.value[key]

        if (contentEl && headerEl && openItems.value[key]) {
          const contentTop = contentEl.getBoundingClientRect().top + scrollTop
          const contentBottom = contentTop + contentEl.offsetHeight
          const headerHeight = headerEl.offsetHeight

          // Check if content is in viewport and header should be sticky
          if (
            scrollTop + headerOffset >= contentTop - headerHeight &&
            scrollTop < contentBottom
          ) {
            activeStickyKey.value = key
          }
        }
      })
    }

    // Use IntersectionObserver for better performance
    const observerOptions = {
      root: null,
      rootMargin: '-80px 0px -50% 0px',
      threshold: [0, 0.1, 0.5, 1]
    }

    const observer = new IntersectionObserver(entries => {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          const key = entry.target.getAttribute('data-project-key')
          if (key && openItems.value[key]) {
            activeStickyKey.value = key
          }
        }
      })
    }, observerOptions)

    // Watch for scroll and open/close changes
    const handleScroll = () => {
      updateActiveSticky()
    }

    window.addEventListener('scroll', handleScroll, { passive: true })

    // Observe all project content areas when they're opened
    watch(
      () => openItems.value,
      () => {
        nextTick(() => {
          Object.keys(projectRefs.value).forEach(key => {
            const el = projectRefs.value[key]
            if (el && openItems.value[key]) {
              observer.observe(el)
            } else if (el) {
              observer.unobserve(el)
            }
          })
          updateActiveSticky()
        })
      },
      { deep: true }
    )

    onUnmounted(() => {
      observer.disconnect()
      window.removeEventListener('scroll', handleScroll)
    })
  })
</script>

<template>
  <div class="min-h-screen">
    <!-- Hero Section -->
    <div class="relative pt-16 sm:pt-24 sm:pb-12 pb-8">
      <div class="mx-auto max-w-7xl px-6 lg:px-8">
        <div class="mx-auto max-w-3xl text-center">
          <h1
            class="text-3xl font-bold tracking-tight text-gray-900 sm:text-5xl dark:text-gray-100"
          >
            PhD Application Portfolio
          </h1>
          <p class="mt-6 text-lg leading-8 text-gray-600 dark:text-gray-400">
            Yutong Han
          </p>
          <!-- <p class="mt-4 text-base leading-6 text-gray-500 dark:text-gray-500">
            Visualizing Complexity: From Evidence to Trust<br />
            Exploring the intersection of Human-AI Collaboration, Visual
            Epistemology, and Civic Media
          </p> -->
        </div>
      </div>
    </div>

    <!-- Research Interests Section -->
    <section class="pb-12 sm:pb-16 sm:pt-8 pt-6">
      <div class="mx-auto max-w-7xl px-6 lg:px-8">
        <div class="mx-auto max-w-3xl">
          <h2
            class="text-2xl font-bold tracking-tight text-gray-900 sm:text-3xl dark:text-gray-100 mb-8"
          >
            Research Interests
          </h2>
          <div class="prose prose-lg dark:prose-invert max-w-none">
            <p class="text-gray-700 dark:text-gray-300 leading-relaxed">
              My research sits at the intersection of
              <strong>Data Visualization</strong>,
              <strong>Urban Informatics</strong>,
              <strong>Spatio-temporal Data Analysis</strong>, and
              <strong>Narrative Visualization</strong>. My work draws on visual
              epistemology. I study how visual representations can reduce the
              trust gap between people and AI systems, ask how people come to
              know and trust information through visual forms, and examine what
              this means for civic media and public engagement.
            </p>
            <p class="text-gray-700 dark:text-gray-300 leading-relaxed mt-4">
              I develop frameworks that make algorithmic processes visible and
              open to scrutiny. I design visual interfaces that support
              transparency and auditability. I aim to strengthen human–AI
              collaboration in urban governance and public policy.
            </p>
          </div>
        </div>
      </div>
    </section>

    <!-- Core Documents Section -->
    <section class="pb-12 sm:pb-16 bg-gray-50 dark:bg-gray-900/50">
      <div class="mx-auto max-w-7xl px-6 lg:px-8">
        <div class="mx-auto max-w-3xl">
          <h2
            class="text-2xl font-bold tracking-tight text-gray-900 sm:text-3xl dark:text-gray-100 mb-8"
          >
            Core Documents
          </h2>
          <div class="space-y-6">
            <UCard class="p-2">
              <div class="flex items-center justify-between">
                <div>
                  <h3
                    class="text-xl font-semibold text-gray-900 dark:text-white"
                  >
                    Curriculum Vitae (CV)
                  </h3>
                  <p class="mt-2 text-sm text-gray-600 dark:text-gray-400">
                    Academic CV with research experience and publications
                  </p>
                </div>
                <UButton
                  color="secondary"
                  variant="solid"
                  size="lg"
                  class="inline-flex items-center gap-2"
                  @click="openPDF('/file/Yutong_Han_CV.pdf')"
                >
                  <UIcon name="i-lucide-download" class="w-5 h-5" />
                  Download PDF
                </UButton>
              </div>
            </UCard>

            <UCard class="p-2">
              <div class="flex items-center justify-between">
                <div>
                  <h3
                    class="text-xl font-semibold text-gray-900 dark:text-white"
                  >
                    Writing Sample
                  </h3>
                  <p class="mt-2 text-sm text-gray-600 dark:text-gray-400">
                    A 3D Interactive Framework for Spatially Coincident Geodata
                  </p>
                  <p class="mt-1 text-xs text-gray-500 dark:text-gray-500">
                    Research paper on OD flow visualization framework (Pillars)
                  </p>
                </div>
                <div class="flex gap-3">
                  <UButton
                    color="primary"
                    variant="solid"
                    size="lg"
                    class="inline-flex items-center gap-2"
                    @click="openPDF('/file/Yutong_Han_Thesis.pdf')"
                  >
                    <UIcon name="i-lucide-download" class="w-5 h-5" />
                    Download PDF
                  </UButton>
                </div>
              </div>
            </UCard>

            <UCard class="p-2">
              <div class="flex items-center justify-between">
                <div>
                  <h3
                    class="text-xl font-semibold text-gray-900 dark:text-white"
                  >
                    Portfolio PDF
                  </h3>
                  <p class="mt-2 text-sm text-gray-600 dark:text-gray-400">
                    Complete portfolio showcasing selected projects and research
                    work
                  </p>
                </div>
                <div class="flex gap-3">
                  <UButton
                    color="secondary"
                    variant="solid"
                    size="lg"
                    class="inline-flex items-center gap-2"
                    @click="openPDF('/file/Yutong_Han_Portfolio.pdf')"
                  >
                    <UIcon name="i-lucide-download" class="w-5 h-5" />
                    Download PDF
                  </UButton>
                </div>
              </div>
            </UCard>
          </div>
        </div>
      </div>
    </section>

    <!-- Selected Projects Section -->
    <section class="pb-12 sm:pb-16 bg-gray-50 dark:bg-gray-900/50">
      <div class="mx-auto max-w-7xl px-6 lg:px-8">
        <div class="mx-auto max-w-4xl">
          <h2
            class="text-2xl font-bold tracking-tight text-gray-900 sm:text-3xl dark:text-gray-100 mb-8"
          >
            Selected Scholarly & Creative Endeavors
          </h2>

          <div class="space-y-4">
            <div
              v-for="project in projects"
              :key="project.key"
              class="border border-gray-200 dark:border-gray-700 rounded-lg overflow-hidden bg-white dark:bg-gray-800"
            >
              <!-- Sticky Header -->
              <div
                :ref="
                  el => {
                    if (el) projectHeaders[project.key] = el as HTMLElement
                  }
                "
                :class="{
                  'sticky top-0 z-10 shadow-md':
                    activeStickyKey === project.key && openItems[project.key]
                }"
                class="bg-white dark:bg-gray-800 border-b border-gray-200 dark:border-gray-700 transition-all"
              >
                <button
                  class="w-full px-6 py-4 hover:bg-gray-50 dark:hover:bg-gray-700/50 transition-colors flex items-center justify-between text-left"
                  @click="toggleItem(project.key)"
                >
                  <div class="flex-1">
                    <h3 class="text-lg font-bold text-gray-900 dark:text-white">
                      {{ project.label }}
                    </h3>
                    <p
                      class="text-sm text-gray-600 dark:text-gray-400 italic mt-1"
                    >
                      {{ project.subtitle }}
                    </p>
                  </div>
                  <UIcon
                    :name="
                      openItems[project.key]
                        ? 'i-lucide-chevron-up'
                        : 'i-lucide-chevron-down'
                    "
                    class="w-5 h-5 text-gray-400 dark:text-gray-500 ml-4 flex-shrink-0 transition-transform"
                  />
                </button>
              </div>

              <!-- Content -->
              <Transition
                enter-active-class="transition duration-300 ease-out"
                enter-from-class="opacity-0 max-h-0"
                enter-to-class="opacity-100 max-h-[5000px]"
                leave-active-class="transition duration-300 ease-in"
                leave-from-class="opacity-100 max-h-[5000px]"
                leave-to-class="opacity-0 max-h-0"
              >
                <div
                  v-show="openItems[project.key]"
                  :ref="
                    el => {
                      if (el) projectRefs[project.key] = el as HTMLElement
                    }
                  "
                  :data-project-key="project.key"
                  class="px-6 pb-6 space-y-5 overflow-hidden"
                >
                  <!-- Overview -->
                  <div>
                    <p
                      class="text-gray-700 dark:text-gray-300 leading-relaxed text-sm"
                    >
                      {{ project.content.overview }}
                    </p>
                  </div>

                  <!-- Key Innovations -->
                  <div>
                    <h4
                      class="text-sm font-semibold text-gray-900 dark:text-white mb-2"
                    >
                      Key Innovations
                    </h4>
                    <ul class="list-disc pl-5 space-y-1">
                      <li
                        v-for="(innovation, idx) in project.content.innovation"
                        :key="idx"
                        class="text-gray-700 dark:text-gray-300 text-sm leading-relaxed"
                      >
                        {{ innovation }}
                      </li>
                    </ul>
                  </div>

                  <!-- Demo / Link / PDF -->
                  <div
                    class="p-4 bg-blue-50 dark:bg-blue-900/20 rounded-lg border border-blue-200 dark:border-blue-800"
                  >
                    <h4
                      class="text-sm font-semibold text-gray-900 dark:text-white mb-3"
                    >
                      Demo & Details
                    </h4>

                    <!-- Video Demo -->
                    <div
                      v-if="project.content.demo.type === 'video'"
                      class="space-y-3"
                    >
                      <video
                        :src="project.content.demo.src"
                        controls
                        class="w-full rounded-lg shadow-md"
                        preload="metadata"
                      >
                        <p class="text-sm text-gray-600 dark:text-gray-400">
                          Your browser doesn't support HTML5 video.
                          <a
                            :href="project.content.demo.src"
                            class="text-blue-600 dark:text-blue-400 hover:underline"
                            target="_blank"
                          >
                            Download video
                          </a>
                        </p>
                      </video>
                      <div class="flex justify-end">
                        <UButton
                          color="primary"
                          variant="outline"
                          size="sm"
                          :to="project.content.demo.link"
                          class="inline-flex items-center gap-2"
                        >
                          <UIcon
                            name="i-lucide-external-link"
                            class="w-4 h-4"
                          />
                          {{ project.content.demo.linkText }}
                        </UButton>
                      </div>
                    </div>

                    <!-- GIF Demo -->
                    <div
                      v-else-if="project.content.demo.type === 'gif'"
                      class="space-y-3"
                    >
                      <img
                        :src="project.content.demo.src"
                        :alt="project.label"
                        class="rounded-lg w-full h-[300px] object-cover object-center"
                        loading="lazy"
                      />
                      <div class="flex justify-end">
                        <UButton
                          color="primary"
                          variant="outline"
                          size="sm"
                          :to="project.content.demo.link"
                          class="inline-flex items-center gap-2"
                        >
                          <UIcon
                            name="i-lucide-external-link"
                            class="w-4 h-4"
                          />
                          {{ project.content.demo.linkText }}
                        </UButton>
                      </div>
                    </div>

                    <!-- PDF Preview -->
                    <div
                      v-else-if="project.content.demo.type === 'pdf'"
                      class="space-y-3"
                    >
                      <div class="pdf-container">
                        <iframe
                          :src="project.content.demo.src"
                          width="100%"
                          height="400px"
                          class="pdf-iframe"
                        />
                      </div>
                      <div class="flex justify-end">
                        <UButton
                          color="primary"
                          variant="outline"
                          size="sm"
                          class="inline-flex items-center gap-2"
                          @click="
                            project.content.demo.src &&
                            openPDF(project.content.demo.src)
                          "
                        >
                          <UIcon
                            name="i-lucide-external-link"
                            class="w-4 h-4"
                          />
                          {{ project.content.demo.linkText }}
                        </UButton>
                      </div>
                      <!-- <div class="flex justify-center">
                        <UButton
                          color="primary"
                          variant="solid"
                          size="lg"
                          class="inline-flex items-center gap-2"
                          @click="
                            project.content.demo.src &&
                            openPDF(project.content.demo.src)
                          "
                        >
                          <UIcon name="i-lucide-download" class="w-5 h-5" />
                          {{ project.content.demo.linkText }}
                        </UButton>
                      </div> -->
                    </div>
                  </div>
                </div>
              </Transition>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Footer Section -->
    <section class="py-12 sm:py-16">
      <div class="mx-auto max-w-7xl px-6 lg:px-8">
        <div class="mx-auto max-w-3xl text-center">
          <p class="text-gray-600 dark:text-gray-400">
            For inquiries, please contact:
            <a
              href="mailto:hanyutong19951123@gmail.com"
              class="text-blue-600 dark:text-blue-400 hover:underline"
            >
              hanyutong19951123@gmail.com
            </a>
          </p>
          <!-- <p class="mt-4 text-sm text-gray-500 dark:text-gray-500">
            Portfolio:
            <a
              href="https://yutonghan19951123.github.io"
              class="text-blue-600 dark:text-blue-400 hover:underline"
              target="_blank"
            >
              https://yutonghan19951123.github.io
            </a>
          </p> -->
        </div>
      </div>
    </section>
  </div>
</template>
