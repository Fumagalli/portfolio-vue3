<script setup lang="ts">
import { computed } from 'vue'
import { cn } from '@/utils/cn'

interface CardContentProps {
  class?: string
}

const props = defineProps<CardContentProps>()

const classes = computed(() => cn('p-6 pt-0', props.class))
</script>

<template>
  <div :class="classes" v-bind="$attrs">
    <slot />
  </div>
</template>
