<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue'
import { useI18n } from 'vue-i18n'
import LanguageSelector from './LanguageSelector.vue'

const { t } = useI18n()
const activeSection = ref('')
const isScrolled = ref(false)

const navItems = [
  { id: 'about', label: t('nav.about') },
  { id: 'projects', label: t('nav.projects') },
  { id: 'experience', label: t('nav.experience') },
  { id: 'testimonials', label: t('nav.testimonials') },
  { id: 'contact', label: t('nav.contact') },
]

const handleScroll = () => {
  isScrolled.value = window.scrollY > 50

  const sections = ['about', 'projects', 'experience', 'testimonials', 'contact']
  const currentSection = sections.find((section) => {
    const element = document.getElementById(section)
    if (element) {
      const rect = element.getBoundingClientRect()
      return rect.top <= 100 && rect.bottom >= 100
    }
    return false
  })

  if (currentSection) {
    activeSection.value = currentSection
  }
}

const scrollToSection = (sectionId: string) => {
  const element = document.getElementById(sectionId)
  if (element) {
    const offset = 80
    const elementPosition = element.getBoundingClientRect().top
    const offsetPosition = elementPosition + window.pageYOffset - offset

    window.scrollTo({
      top: offsetPosition,
      behavior: 'smooth',
    })
  }
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll)
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})
</script>

<template>
  <nav
    :class="[
      'fixed top-0 left-0 right-0 z-40 transition-all duration-300',
      isScrolled
        ? 'bg-card/95 backdrop-blur-md shadow-md py-4'
        : 'bg-transparent py-6'
    ]"
  >
    <div class="container mx-auto px-4">
      <div class="flex items-center justify-between">
        <div class="flex-1" />

        <ul class="flex flex-wrap gap-2 justify-center md:gap-6">
          <li v-for="item in navItems" :key="item.id">
            <button
              @click="scrollToSection(item.id)"
              :class="[
                'px-4 py-2 rounded-full font-medium transition-all',
                activeSection === item.id
                  ? 'bg-accent text-accent-foreground'
                  : 'text-muted-foreground hover:text-accent hover:bg-accent/10'
              ]"
            >
              {{ item.label }}
            </button>
          </li>
        </ul>

        <div class="flex-1 flex justify-end">
          <LanguageSelector />
        </div>
      </div>
    </div>
  </nav>
</template>
