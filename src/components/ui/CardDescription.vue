<script setup lang="ts">
import { computed } from 'vue'
import { cn } from '@/utils/cn'

interface CardDescriptionProps {
  class?: string
}

const props = defineProps<CardDescriptionProps>()

const classes = computed(() => cn('text-sm text-muted-foreground', props.class))
</script>

<template>
  <p :class="classes" v-bind="$attrs">
    <slot />
  </p>
</template>
