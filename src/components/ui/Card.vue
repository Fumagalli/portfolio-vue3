<script setup lang="ts">
import { computed } from 'vue'
import { cn } from '@/utils/cn'

interface CardProps {
  class?: string
}

const props = defineProps<CardProps>()

const classes = computed(() => cn('rounded-lg border bg-card text-card-foreground shadow-sm', props.class))
</script>

<template>
  <div :class="classes" v-bind="$attrs">
    <slot />
  </div>
</template>
