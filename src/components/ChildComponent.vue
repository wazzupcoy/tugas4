<template>
  <div>
    <h3>Food Component</h3>
    <ul>
      <li v-for="(food, index) in foodList" :key="index">{{ food }}</li>
    </ul>
    <button @click="sendFood">Send Food to Parent</button>
  </div>
</template>

<script setup>
import { ref, defineEmits } from 'vue'

const emit = defineEmits(['response'])

const foodList = ref(['Pizza', 'Burger', 'Pasta'])

function sendFood() {
  if (foodList.value.length > 0) {
    const food = foodList.value.shift()
    emit('response', `Sent ${food} to parent`)
  } else {
    emit('response', 'No food available')
  }
}
</script>

<style scoped>
/* Add necessary styles here */
</style>
