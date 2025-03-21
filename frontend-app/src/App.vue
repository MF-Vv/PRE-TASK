<script setup>
import { ref, onMounted } from 'vue'
import axios from 'axios'

const message = ref('')

onMounted(async () => {
  try {
    const response = await axios.get('http://159.223.78.177:5000') // Update with your backend URL
    message.value = response.data.message
    console.log(message.value)
  } catch (error) {
    console.error('Error fetching data:', error)
  }
})
</script>

<template>
  <div
    class="min-h-screen flex flex-col items-center justify-center bg-blue-500 text-white text-2xl"
  >
    <h2>Hello, DevOps CI/CDDdd</h2>
    <p>Message: {{ message }}</p>
  </div>
</template>
