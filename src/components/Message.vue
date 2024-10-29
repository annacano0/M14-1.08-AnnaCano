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
  <input
    v-model="newMessage"
    type="text"
    placeholder="Escriu el teu missatge"
  />
  <button @click="managePostMessage">Envia</button>
</template>

<style scoped></style>
