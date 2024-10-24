<script setup>
import { ref } from 'vue'

const props = defineProps({
  logedUser: String,
})

let user = props.logedUser
let newMessage = ref('')

const emit = defineEmits(['postMessage'])
const managePostMessage = () => {
  console.log(user + ' ' + newMessage.value)

  emit('postMessage', { user, newMessage })
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
