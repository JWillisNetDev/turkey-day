<template>
  <div class="gap-4">
    <h3 class="text-center font-serif text-3xl tracking-wider">{{ title }}</h3>
    <p v-if="subtitle" class="text-center font-serif text-sm tracking-wider">{{ subtitle }}</p>
  </div>
</template>

<script setup lang="ts">
import { defineProps } from 'vue'

interface MenuItemProps {
  title: string
  subtitle?: string
}

defineProps<MenuItemProps>()
</script>

<style scoped></style>
