<script setup lang="ts">
import { ref, computed } from 'vue'
import { useI18n } from 'vue-i18n'
import { useIntersectionObserver } from '@/composables/useIntersectionObserver'
import Card from '@/components/ui/Card.vue'
import { Briefcase, CheckCircle2 } from 'lucide-vue-next'

interface TimelineItem {
  company: string
  role: string
  period: string
  achievements: string[]
}

const { t, tm } = useI18n()
const sectionRef = ref<HTMLElement | null>(null)
const { isInView } = useIntersectionObserver(sectionRef, { threshold: 0.1, triggerOnce: true })

const timeline = computed(() => {
  const data = tm('experience.timeline')
  return Array.isArray(data) ? (data as TimelineItem[]) : []
})
</script>

<template>
  <section id="experience" class="py-20">
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
            {{ t('experience.title') }}
          </h2>

          <p class="text-lg text-muted-foreground">
            {{ t('experience.subtitle') }}
          </p>
        </div>

        <div class="space-y-8">
          <Card
            v-for="(job, index) in timeline"
            :key="index"
            class="p-8 border-l-4 border-accent bg-card hover:shadow-lg transition-smooth"
          >
            <div class="flex items-start gap-4 mb-4">
              <div class="p-3 rounded-lg bg-accent/10 flex-shrink-0">
                <Briefcase class="w-6 h-6 text-accent" />
              </div>

              <div class="flex-1">
                <h3 class="text-2xl font-bold text-card-foreground mb-1">
                  {{ job.role }}
                </h3>

                <p class="text-accent font-semibold mb-1">
                  {{ job.company }}
                </p>

                <p class="text-sm text-muted-foreground">
                  {{ job.period }}
                </p>
              </div>
            </div>

            <ul class="space-y-3">
              <li
                v-for="(achievement, achIndex) in job.achievements"
                :key="achIndex"
                class="flex items-start gap-3 text-muted-foreground"
              >
                <CheckCircle2 class="w-5 h-5 text-accent flex-shrink-0 mt-0.5" />
                <span>{{ achievement }}</span>
              </li>
            </ul>
          </Card>
        </div>
      </div>
    </div>
  </section>
</template>
