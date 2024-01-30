<template>
  <form class="FormInfo">
    <h3 class="titule">Contact us</h3>

    <div :class="{ 'input-container': true, 'success-container': isNameValid() }">
      <input :class="{ error: !isNameValid(), success: isNameValid() }" id="name" placeholder="Full Name" type="text" v-model="name" @input="handleNameInput">
      <span v-if="isNameValid() && name" class="success-mark">✅</span>
    </div>

    <div :class="{ 'input-container': true, 'success-container': isAgeValid() }">
      <input :class="{ error: !isAgeValid(), success: isAgeValid() }" id="age" type="number" placeholder="Age" v-model="age">
      <span v-if="isAgeValid()" class="success-mark">✅</span>
    </div>

    <select name="gender" id="gender" v-model="gender">
      <option disabled value="">Select one option</option>
      <option value="male">Male</option>
      <option value="female">Female</option>
      <option value="nonbinary">Nonbinary</option>
    </select>

    <div :class="{ 'input-container': true, 'success-container': isPhoneValid() }">
      <input :class="{ error: !isPhoneValid(), success: isPhoneValid() }" id="phone" type="tel" placeholder="Phone" v-model="phone" @input="handlePhoneInput">
      <span v-if="isPhoneValid()" class="success-mark">✅</span>
    </div>

    <button class="button" type="submit">Send</button>
  </form>
</template>

<script lang="ts" setup>
import type IFormItem from '@/interface/IFormItem';
import router from '@/router';
import { ref } from 'vue';

const routeViews = router.options.routes.filter(route => {
  return { name: route.name };
}) as IFormItem[];

const name = ref('');
const age = ref('');
const gender = ref(null);
const phone = ref('');
const error = ref(true);

const isNameValid = () => name.value.length <= 18;

const isAgeValid = () => {
  const ageNumber = parseInt(age.value);
  return !isNaN(ageNumber) && ageNumber >= 1 && ageNumber <= 60;
};

const isPhoneValid = () => phone.value.length === 10 && /^\d+$/.test(phone.value);

const handlePhoneInput = () => {
  phone.value = phone.value;
};

const handleNameInput = () => {
  name.value = name.value.trim();
};

</script>

<style>
.FormInfo {
  display: flex;
  flex-direction: column;
  justify-content: center;
  width: 100%;
  background-color: #f2f2f2;
  border-radius: 10px;
  padding: 40px;
}

input {
  padding: 10px;
  margin: 10px 0px;
  border-radius: 5px;
  width: 100%;
  border: 0px;
}

input :active {
  border: 1px solid #2a21d3;
}

select {
  padding: 10px;
  margin: 10px 0px;
  border: 0px;
}
.error {
  color: #ff5555;
}

.titule {
  color: #0b0c0e;
  font-size: 30px;
  margin-bottom: 20px;
  font-weight: 800;
  text-align: center;
}

.button{
  padding: 10px;
  margin: 10px 0px;
  background-color: #047de5;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  font-weight: 600;
  font-size: 16px;
  color: #f0f7fd;
}

.button:hover{
  background-color: #0361b2;
}

.success {
  color: #00aa00;
}
.input-container {
  position: relative;
}

.success-container {
  color: #00aa00;
}

.success-mark {
  position: absolute;
  right: 10px;
  top: 50%;
  transform: translateY(-50%);
  font-size: 20px;
}

</style>
