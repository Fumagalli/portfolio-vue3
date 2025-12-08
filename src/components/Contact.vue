<script setup lang="ts">
import { ref } from 'vue'
import { useI18n } from 'vue-i18n'
import { useIntersectionObserver } from '@/composables/useIntersectionObserver'
import { Mail, Linkedin } from 'lucide-vue-next'

const { t } = useI18n()
const sectionRef = ref<HTMLElement | null>(null)
const { isInView } = useIntersectionObserver(sectionRef, { threshold: 0.1, triggerOnce: true })
</script>

<template>
  <section id="contact" class="py-20 bg-secondary/30">
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
            {{ t('contact.title') }}
          </h2>

          <p class="text-lg text-muted-foreground mb-8">
            {{ t('contact.subtitle') }}
          </p>

          <div class="flex flex-wrap gap-4 justify-center mb-12">
            <a
              href="mailto:contato@afumagalli.com.br"
              class="inline-flex items-center gap-2 text-accent hover:text-accent/80 transition-smooth font-medium"
            >
              <Mail class="w-5 h-5" />
              <span>contato@afumagalli.com.br</span>
            </a>

            <span class="text-muted-foreground">•</span>

            <a
              href="mailto:fumagalli.angelo@gmail.com"
              class="inline-flex items-center gap-2 text-accent hover:text-accent/80 transition-smooth font-medium"
            >
              <Mail class="w-5 h-5" />
              <span>fumagalli.angelo@gmail.com</span>
            </a>

            <span class="text-muted-foreground">•</span>

            <a
              href="https://linkedin.com/in/a-fumagalli-rs"
              target="_blank"
              rel="noopener noreferrer"
              class="inline-flex items-center gap-2 text-accent hover:text-accent/80 transition-smooth font-medium"
            >
              <Linkedin class="w-5 h-5" />
              <span>linkedin.com/in/a-fumagalli-rs</span>
            </a>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
