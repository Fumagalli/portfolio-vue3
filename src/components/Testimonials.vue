<script setup lang="ts">
import { ref, computed } from 'vue'
import { useI18n } from 'vue-i18n'
import { useIntersectionObserver } from '@/composables/useIntersectionObserver'
import Card from '@/components/ui/Card.vue'
import { Quote, Users, Briefcase } from 'lucide-vue-next'

interface Testimonial {
  name: string
  role: string
  relationship: string
  text: string
}

const { t, tm } = useI18n()
const sectionRef = ref<HTMLElement | null>(null)
const { isInView } = useIntersectionObserver(sectionRef, { threshold: 0.1, triggerOnce: true })

const testimonials = computed(() => {
  const data = tm('testimonials.items')
  return Array.isArray(data) ? (data as Testimonial[]) : []
})
</script>

<template>
  <section id="testimonials" class="py-20 bg-secondary/30">
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
            {{ t('testimonials.title') }}
          </h2>

          <p class="text-lg text-muted-foreground">
            {{ t('testimonials.subtitle') }}
          </p>
        </div>

        <div class="grid grid-cols-1 gap-8 md:grid-cols-2">
          <Card
            v-for="(testimonial, index) in testimonials"
            :key="index"
            class="p-8 bg-card hover:shadow-lg transition-smooth relative"
          >
            <Quote class="w-12 h-12 text-accent/20 absolute top-6 right-6" />

            <div class="relative z-10">
              <p class="text-muted-foreground mb-6 leading-relaxed italic">
                "{{ testimonial.text }}"
              </p>

              <div class="flex items-start gap-3">
                <div class="p-2 rounded-full bg-accent/10 flex-shrink-0">
                  <Users class="w-5 h-5 text-accent" />
                </div>

                <div>
                  <p class="font-bold text-card-foreground">
                    {{ testimonial.name }}
                  </p>

                  <p class="text-sm text-muted-foreground">
                    {{ testimonial.role }}
                  </p>

                  <div class="flex items-center gap-2 mt-1 text-xs text-accent">
                    <Briefcase class="w-3 h-3" />
                    <span>{{ testimonial.relationship }}</span>
                  </div>
                </div>
              </div>
            </div>
          </Card>
        </div>
      </div>
    </div>
  </section>
</template>
