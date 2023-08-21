<script setup lang="ts">
  defineProps<{
    text: string
  }>()
</script>

<template>
  <button class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded text-sm sm:text-base">
    {{ text }}
  </button>
</template>