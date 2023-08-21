<script setup lang="ts">
import HeaderComponent from './components/HeaderComponent.vue';
import CardComponent from './components/CardComponent.vue';
import ButtonComponent from './components/ButtonComponent.vue';
</script>

<template>
  <HeaderComponent />
  <main>
    <CardComponent v-if="quote != ''" v-bind:quote="quote" />
    <ButtonComponent text="Gerar Quote"/>
  </main>
</template>

<script lang="ts">
  export default {
  data() {
    return {
      quote: ""
    }
  }
}
</script>