<template>
  <div>
    <h2>Customer Component</h2>
    <button @click="requestFood">Request Food from Child</button>
    <p>{{ warningMessage }}</p>
    <h3>Foods:</h3>
    <ul>
      <li v-for="(food, index) in foods" :key="index">{{ food }}</li>
    </ul>
    <ChildComponent @response="handleResponse" />
    <slot name="extra-content"></slot>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import ChildComponent from './ChildComponent.vue'

const foods = ref([])
const warningMessage = ref('')

function addFood(food) {
  foods.value.push(food)
  warningMessage.value = ''
}

function showWarning(message) {
  warningMessage.value = message
}

function requestFood() {
  showWarning('Requesting food from child...')
}

function handleResponse(message) {
  alert(message)
  showWarning(message)
  if (message.startsWith('Sent')) {
    const food = message.split(' ')[1]
    addFood(food)
  }
}
</script>

<style scoped>
/* Add necessary styles here */
</style>
