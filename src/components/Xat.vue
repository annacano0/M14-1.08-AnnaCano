<script setup>
import { ref } from 'vue'
import Message from './Message.vue'

let messages = ref([])

const logedUser = 'Anna'

const postMessage = newMessage => {
  if(validateMessage(newMessage.text))messages.value.push(newMessage)
}

const validateMessage=(messageText)=>{
  if(
  typeof messageText=== 'string' && 
  messageText.trim() !== '' && 
  messageText.trim().length >= 1 
  ) return true 
  return false  
}
</script>

<template>
  <h1>Xat entre usuaris</h1>
  <ul class="message-container">
    <li v-for="(message, index) in messages" :key="index">
      {{ message.user }}: {{ message.text }}
    </li>
  </ul>  
  <Message :logedUser="logedUser" @sendMessage="postMessage" />
</template>

<style scoped></style>
