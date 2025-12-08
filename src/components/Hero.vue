<script setup lang="ts">
import { useI18n } from 'vue-i18n'
import Button from '@/components/ui/Button.vue'
import { MapPin, Github, Linkedin } from 'lucide-vue-next'

interface HeroProps {
  onProjectsClick?: () => void
  onContactClick?: () => void
}

const props = defineProps<HeroProps>()
const { t } = useI18n()

const scrollToProjects = () => {
  if (props.onProjectsClick) {
    props.onProjectsClick()
  }
}

const scrollToContact = () => {
  if (props.onContactClick) {
    props.onContactClick()
  }
}
</script>

<template>
  <section class="min-h-screen flex items-center justify-center relative overflow-hidden">
    <div class="absolute inset-0 gradient-hero opacity-10" />

    <div class="container mx-auto px-4 py-20 relative z-10">
      <div class="max-w-6xl mx-auto text-center animate-fade-in-up">
        <h1 class="text-5xl font-bold mb-6 text-foreground md:text-7xl">
          {{ t('hero.title') }}
        </h1>

        <p class="text-xl text-muted-foreground mb-6 leading-relaxed md:text-2xl">
          {{ t('hero.subtitle') }}
        </p>

        <div class="flex items-center justify-center gap-2 text-muted-foreground mb-10">
          <MapPin class="w-5 h-5" />
          <span class="text-lg">{{ t('hero.location') }}</span>
        </div>

        <div class="flex flex-col sm:flex-row gap-4 justify-center items-center mb-10">
          <Button
            size="lg"
            class="gradient-accent text-accent-foreground hover:opacity-90 transition-smooth px-8 py-6 text-lg font-semibold shadow-elegant"
            @click="scrollToProjects"
          >
            {{ t('hero.cta_projects') }}
          </Button>

          <Button
            size="lg"
            variant="outline"
            class="border-2 border-accent text-accent hover:bg-accent hover:text-accent-foreground transition-smooth px-8 py-6 text-lg font-semibold"
            @click="scrollToContact"
          >
            {{ t('hero.cta_contact') }}
          </Button>
        </div>

        <div class="flex gap-6 justify-center">
          <a
            href="https://github.com/Fumagalli"
            target="_blank"
            rel="noopener noreferrer"
            class="text-muted-foreground hover:text-accent transition-smooth"
            aria-label="GitHub"
          >
            <Github class="w-8 h-8" />
          </a>

          <a
            href="https://linkedin.com/in/a-fumagalli-rs"
            target="_blank"
            rel="noopener noreferrer"
            class="text-muted-foreground hover:text-accent transition-smooth"
            aria-label="LinkedIn"
          >
            <Linkedin class="w-8 h-8" />
          </a>
        </div>
      </div>
    </div>
  </section>
</template>
