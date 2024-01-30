<script setup lang="ts">
import { ref } from 'vue';
import FormInfo from '@/components/Form/FormInfo.vue';

const name = ref('');
const error = ref(true);

const checkValidation =() => {
  if(name.value.length < 5) {
    error.value = false;
  } else {
    error.value = true;
  }
}
</script>

<template>
  <main>
    <FormInfo></FormInfo>
    <h2>This is Home!</h2>
    <h3>Mi name is</h3>
    <input :on-input="checkValidation()" type="text" v-model="name">
    <h1 :class="{ error:error }">{{ name }}</h1>
    
  </main>
</template>

