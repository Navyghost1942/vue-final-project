<script setup>
import axios from 'axios'
import { ref } from 'vue'

const api = axios.create({
  baseURL: import.meta.env.VITE_API_URL,
  auth: {
    username: import.meta.env.VITE_API_USERNAME,
    password: import.meta.env.VITE_API_PASSWORD,
  },
})


const coffeeName = ref('')
const coffeeImage = ref('')
  
const addCoffee = async () => {
  const { data } = await api.post('/api/coffees', {
    name: coffeeName.value,
    image: coffeeImage.value
  })
}
</script>

<template>
  <form class="login-form" @submit.prevent="addCoffee">
    <input v-model="coffeeName" type="text" placeholder="name" />
    <input v-model="coffeeImage" type="text" placeholder="image" />
    <button type="submit" class="bg-green-500 px-4 py-2">submit</button>
  </form>
</template>

<style scoped lang="postcss">
  .login-form {
    @apply mx-auto mt-80 flex max-w-md flex-col gap-4 rounded-md bg-white p-8 shadow-lg;
    & input {
      @apply rounded-md px-4 py-2 text-xl ring-1 ring-slate-300;
    }
  }
</style>





