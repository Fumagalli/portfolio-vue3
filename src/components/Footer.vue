<script setup lang="ts">
import { computed } from 'vue'
import { useI18n } from 'vue-i18n'
import { GraduationCap, Languages, BookOpen } from 'lucide-vue-next'

const { t } = useI18n()

const languageItems = computed(() => {
  const items = t('footer.languages.items', { returnObjects: true })
  return Array.isArray(items) ? (items as string[]) : []
})
</script>

<template>
  <footer class="py-12 border-t border-border bg-card">
    <div class="container mx-auto px-4">
      <div class="max-w-6xl mx-auto">
        <div class="grid grid-cols-1 gap-8 mb-8 md:grid-cols-3">
          <!-- Educação -->
          <div>
            <div class="flex items-center gap-2 mb-4">
              <GraduationCap class="w-6 h-6 text-accent" />
              <h3 class="text-xl font-bold text-card-foreground">
                {{ t('footer.education.title') }}
              </h3>
            </div>

            <p class="text-muted-foreground mb-1">
              <strong>{{ t('footer.education.degree') }}</strong>
            </p>

            <p class="text-sm text-muted-foreground mb-2">
              {{ t('footer.education.institution') }} • {{ t('footer.education.year') }}
            </p>
          </div>

          <!-- Cursos -->
          <div>
            <div class="flex items-center gap-2 mb-4">
              <BookOpen class="w-6 h-6 text-accent" />
              <h3 class="text-xl font-bold text-card-foreground">
                {{ t('footer.education.course.title') }}
              </h3>
            </div>

            <p class="text-sm text-muted-foreground">
              <!-- Safe: controlled content from translation files -->
              <span v-html="t('footer.education.course.courses')" />
            </p>
          </div>

          <!-- Idiomas -->
          <div>
            <div class="flex items-center gap-2 mb-4">
              <Languages class="w-6 h-6 text-accent" />
              <h3 class="text-xl font-bold text-card-foreground">
                {{ t('footer.languages.title') }}
              </h3>
            </div>

            <ul class="space-y-1 text-muted-foreground">
              <li v-for="(language, index) in languageItems" :key="index">
                {{ language }}
              </li>
            </ul>
          </div>
        </div>

        <div class="pt-8 border-t border-border text-center text-sm text-muted-foreground">
          <p>
            © {{ new Date().getFullYear() }} aFumagalli. {{ t('footer.rights') }}
          </p>
        </div>
      </div>
    </div>
  </footer>
</template>
