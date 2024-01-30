<template>
        <input :on-input="checkValidation()" class="input-form" type="text" v-model="name">
        <h1 :class="{ error:error }">{{ name }}</h1>
</template>
<script lang="ts" setup>
import { ref } from 'vue';
import type IFormItem from '@/interface/IFormItem';

const data = defineProps<IFormItem>();

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
<style>
.error {
  color: #ff5555;
}
</style>