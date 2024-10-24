<script setup>
import { ref } from 'vue'
import Message from './Message.vue'
let messages = ref([])

const logedUser = 'Anna'

const postMessage = newMessage => {
  console.log('posting message')
  messages.value.push(newMessage)
}
</script>

<template>
  <h1>Xat entre usuaris</h1>
  <ul class="message-container">
    <li v-for="(message, index) in messages" :key="index">
      {{ message.user }}{{ message.text }}
    </li>
  </ul>
  <Message :logedUser="logedUser" :post-message="postMessage" />
</template>

<style scoped></style>
