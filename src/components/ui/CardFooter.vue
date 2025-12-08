<script setup lang="ts">
import { computed } from 'vue'
import { cn } from '@/utils/cn'

interface CardFooterProps {
  class?: string
}

const props = defineProps<CardFooterProps>()

const classes = computed(() => cn('flex items-center p-6 pt-0', props.class))
</script>

<template>
  <div :class="classes" v-bind="$attrs">
    <slot />
  </div>
</template>
