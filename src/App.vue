<script setup lang="ts">
import axios from 'axios';
import HeaderComponent from './components/HeaderComponent.vue';
import CardComponent from './components/CardComponent.vue';
import ButtonComponent from './components/ButtonComponent.vue';
</script>

<template>
  <HeaderComponent />
  <main>
    <div v-if="image != ''" class="w-1/4 mx-auto p-4">
      <img v-bind:src="image">
    </div>
    <CardComponent v-if="quote != ''" v-bind:quote="quote" />
    <div class="flex mx-auto w-1/2 justify-evenly">
      <ButtonComponent @click="handleQuoteImage" class="mt-4" text="Gerar Quote"/>
      <ButtonComponent @click="translateQuote" class="mt-4" text="Traduzir"/>
    </div>
  </main>
</template>

<script lang="ts">
  export default {
  data() {
    return {
      quote: "",
      image: ""
    }
  },
  methods: {
    async getQuote() {
      const response = await axios.get('https://api.kanye.rest/');
      this.quote = response.data.quote;
    },
    async translateQuote() {
        const response = await axios.get(
          `https://translate.googleapis.com/translate_a/single?client=gtx&sl=auto&tl=pt&dt=t&q=${encodeURIComponent(this.quote)}`
        );
        const translatedQuote = await response.data;
        this.quote = translatedQuote[0][0][0];
    },
    async getDogImage() {
    const dogImage = await axios.get('https://dog.ceo/api/breeds/image/random');
    this.image = dogImage.data.message;
    },

    async handleQuoteImage() {
      await this.getDogImage();
      await this.getQuote();
    }
  },
}
</script>