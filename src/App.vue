<script setup lang="ts">
import { RouterView } from 'vue-router'
</script>

<template>
  <header></header>
  <div class="min-h-dvh">
    <main class="mx-auto w-full max-w-5x1">
      <RouterView />
    </main>
  </div>
</template>

<style scoped></style>
