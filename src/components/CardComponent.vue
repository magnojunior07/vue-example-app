<script setup lang="ts">
  defineProps<{
    quote: string
  }>()
</script>

<template>
  <div class="bg-gray-200 w-2/5 p-8 rounded-lg mx-auto">
    <p>
      {{ quote }}
    </p>
    <p class="text-end pt-2 px-4 text-sm">
      - Kanye West
    </p>
  </div>  
</template>