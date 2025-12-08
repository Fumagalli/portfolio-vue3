<script setup lang="ts">
import { ref } from 'vue'
import { useI18n } from 'vue-i18n'
import { useIntersectionObserver } from '@/composables/useIntersectionObserver'
import { Sparkles, Target, Users, Award } from 'lucide-vue-next'

const { t } = useI18n()
const sectionRef = ref<HTMLElement | null>(null)
const { isInView } = useIntersectionObserver(sectionRef, { threshold: 0.1, triggerOnce: true })

const highlights = [
  {
    icon: Award,
    text: t('about.highlights.experience'),
  },
  {
    icon: Target,
    text: t('about.highlights.focus'),
  },
  {
    icon: Users,
    text: t('about.highlights.international'),
  },
  {
    icon: Sparkles,
    text: t('about.highlights.mentorship'),
  },
]
</script>

<template>
  <section id="about" class="py-20 bg-secondary/30">
    <div class="container mx-auto px-4">
      <div
        ref="sectionRef"
        :class="[
          'max-w-6xl mx-auto transition-all duration-700',
          isInView ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-10'
        ]"
      >
        <h2 class="text-4xl font-bold text-center mb-6 text-foreground md:text-5xl">
          <!-- Safe: controlled content from translation files -->
          <span v-html="t('about.title')" />
        </h2>

        <p class="text-lg text-muted-foreground text-justify mb-12 leading-relaxed md:text-xl">
          <!-- Safe: controlled content from translation files -->
          <span v-html="t('about.description')" />
        </p>

        <div class="grid grid-cols-1 gap-6 md:grid-cols-2">
          <div
            v-for="(highlight, index) in highlights"
            :key="index"
            class="flex items-start gap-4 p-6 bg-card rounded-lg border hover:shadow-lg transition-smooth"
          >
            <div class="p-3 rounded-lg bg-accent/10 flex-shrink-0">
              <component :is="highlight.icon" class="w-6 h-6 text-accent" />
            </div>
            <p class="text-card-foreground leading-relaxed">
              {{ highlight.text }}
            </p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
