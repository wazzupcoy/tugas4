<template>
  <main>
    <ParentComponent @display-data="handleDisplayData">
      <template v-slot:extra-content>
        <div>This is extra content from slot!</div>
      </template>
    </ParentComponent>
    <p>{{ dataFromChild }}</p>
  </main>
</template>

<script setup>
import { ref } from 'vue'
import ParentComponent from './components/ParentComponent.vue'

const dataFromChild = ref('')

function handleDisplayData(data) {
  dataFromChild.value = data
}
</script>

<style scoped>
/* Add any necessary styles here */
</style>
