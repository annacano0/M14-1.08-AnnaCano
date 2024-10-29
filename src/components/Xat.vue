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
  <div id="xat-container">
    <h1>Xat entre usuaris</h1>
    <ul class="message-container">
      <li v-for="(message, index) in messages" :key="index">
        <span>{{ message.user }}:</span> {{ message.text }}
      </li>
    </ul>  
    <Message :logedUser="logedUser" @sendMessage="postMessage" />
  </div>
 
</template>

<style scoped>

#xat-container{
background-color: rgb(82, 82, 82);
border-radius: 10px;
margin: 10px;
padding: 10px 20px 20px;
display: flex;
flex-direction: column;
justify-content: center;
text-align: center;
}

ul{
  list-style: none;
  text-align: left;
  display: flex;
  flex-direction: column;
  padding: 0px;
}

li{
  color: black;
  font-weight: bold;
  background-color: white;
  border-radius: 10px;
  padding: 5px;
  width: fit-content;
  margin: 5px;
}

li span{
  color: rgb(63, 63, 63);
}
</style>
