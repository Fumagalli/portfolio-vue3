<script setup lang="ts">
import { useI18n } from 'vue-i18n'
import { useRouter } from 'vue-router'

const { t } = useI18n()
const router = useRouter()

const goHome = () => {
  router.push('/')
}
</script>

<!-- aplicar i18n aos textos dessa página -->
<template>
  <div class="min-h-screen flex items-center justify-center bg-background">
    <div class="text-center px-4">
      <h1 class="text-9xl font-bold text-primary mb-4">404</h1>

      <h2 class="text-3xl font-semibold text-foreground mb-4">Página não encontrada</h2>

      <p class="text-muted-foreground mb-8">
        A página que você está procurando não existe ou foi movida.
      </p>

      <button @click="goHome"
        class="px-6 py-3 bg-primary text-primary-foreground rounded-lg hover:opacity-90 transition-smooth">
        Voltar para Home
      </button>
    </div>
  </div>
</template>
