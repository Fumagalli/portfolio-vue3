<script setup lang="ts">
import { ref, computed } from 'vue'
import { useI18n } from 'vue-i18n'
import { useIntersectionObserver } from '@/composables/useIntersectionObserver'
import Card from '@/components/ui/Card.vue'
import Badge from '@/components/ui/Badge.vue'
import { Code2, TrendingUp } from 'lucide-vue-next'

interface Project {
  name: string
  description: string
  impact: string
  tech: string[]
  url?: string
  github?: string
}

const { t, tm } = useI18n()
const sectionRef = ref<HTMLElement | null>(null)
const { isInView } = useIntersectionObserver(sectionRef, { threshold: 0.1, triggerOnce: true })

const projects = computed(() => {
  const projectsData = tm('projects.items')
  return Array.isArray(projectsData) ? (projectsData as Project[]) : []
})
</script>

<template>
  <section id="projects" class="py-20">
    <div class="container mx-auto px-4">
      <div
        ref="sectionRef"
        :class="[
          'max-w-6xl mx-auto transition-all duration-700',
          isInView ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-10'
        ]"
      >
        <div class="text-center mb-12">
          <h2 class="text-4xl font-bold mb-4 text-foreground md:text-5xl">
            {{ t('projects.title') }}
          </h2>

          <p class="text-lg text-muted-foreground">
            {{ t('projects.subtitle') }}
          </p>
        </div>

        <div class="grid grid-cols-1 gap-8 md:grid-cols-2">
          <Card
            v-for="(project, index) in projects"
            :key="index"
            class="p-8 hover:shadow-lg transition-smooth border-border bg-card group"
          >
            <div class="mb-4">
              <Code2 class="w-10 h-10 text-accent mb-4" />

              <h3 class="text-2xl font-bold mb-4 text-card-foreground group-hover:text-accent transition-smooth">
                {{ project.name }}
              </h3>
            </div>

            <p class="text-muted-foreground mb-4 leading-relaxed">
              {{ project.description }}
            </p>

            <div class="flex items-start gap-2 mb-6 p-4 bg-accent/5 rounded-lg border border-accent/20">
              <TrendingUp class="w-5 h-5 text-accent flex-shrink-0 mt-0.5" />

              <p class="text-sm text-card-foreground font-medium">
                {{ project.impact }}
              </p>
            </div>

            <div class="flex flex-wrap gap-2 mb-6">
              <Badge
                v-for="(tech, techIndex) in project.tech"
                :key="techIndex"
                variant="secondary"
                class="bg-secondary text-secondary-foreground"
              >
                {{ tech }}
              </Badge>
            </div>

            <div class="flex flex-wrap gap-3 mt-auto">
              <a
                v-if="project.url"
                :href="project.url"
                target="_blank"
                rel="noopener noreferrer"
                class="inline-flex items-center gap-2 px-4 py-2 bg-accent text-accent-foreground rounded-md hover:bg-accent/90 transition-smooth text-sm font-medium"
              >
                {{ t('projects.view_live') }}
              </a>

              <a
                v-if="project.github"
                :href="project.github"
                target="_blank"
                rel="noopener noreferrer"
                class="inline-flex items-center gap-2 px-4 py-2 border border-border rounded-md hover:bg-secondary transition-smooth text-sm font-medium"
              >
                {{ t('projects.view_github') }}
              </a>
            </div>
          </Card>
        </div>
      </div>
    </div>
  </section>
</template>
