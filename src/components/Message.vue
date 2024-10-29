<script setup>
import { ref } from 'vue'

const props = defineProps({
  logedUser: String,
  sendMessage: Function
})

let user = props.logedUser
let newMessage = ref('')

const emit = defineEmits(['sendMessage'])
const managePostMessage = () => {
  emit('sendMessage', { user, text: newMessage.value })
  newMessage.value = ''
}
</script>

<template>
  <div class="message-container">
     <input
      v-model="newMessage"
      type="text"
      placeholder="Escriu el teu missatge"
    />
    <button @click="managePostMessage">Envia</button>
  </div>
  
</template>

<style scoped>
.message-container{
  margin: 5px 0px;
}
input{
  padding: 10px;
  font-size: 16px;
  border: 1px solid #ddd;
  border-radius: 5px;
  outline: none;
  transition: border-color 0.3s ease;
}

button{
  padding: 10px 20px;
  font-size: 16px;
  color: white;
  background-color: #51c051;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s ease;
  margin-left: 5px;
}
button:hover{
  background-color: #45a045;
}

button:active{
  background-color: #3e913e;
}
</style>
