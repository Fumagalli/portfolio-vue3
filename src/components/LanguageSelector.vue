<script setup lang="ts">
import { useI18n } from 'vue-i18n'
import { Languages } from 'lucide-vue-next'

const { locale } = useI18n()

const toggleLanguage = () => {
  locale.value = locale.value === 'pt' ? 'en' : 'pt'
}
</script>

<template>
  <button
    @click="toggleLanguage"
    class="flex items-center gap-2 px-4 py-2 rounded-full bg-accent/10 hover:bg-accent/20 text-accent border border-accent/30 transition-all font-medium"
    :title="locale === 'pt' ? 'Mudar para Inglês' : 'Switch to Portuguese'"
  >
    <Languages class="w-4 h-4" />
    <span class="text-sm font-semibold uppercase">{{ locale }}</span>
  </button>
</template>
