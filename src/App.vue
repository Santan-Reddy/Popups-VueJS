<script setup>
import Popup from './components/Popup.vue'
import {ref,onMounted} from 'vue'

const triggers = ref({
  buttonsTrigger:false,
  timedTrigger:false
})
onMounted(() => {
  setTimeout(() => {
    triggers.value.timedTrigger = true
  }, 3000)
})
const toggleTrigger=(trigger)=>{
  triggers.value[trigger]=!triggers.value[trigger]
}
</script>

<template>
  <main>
    <h1>Vue Popup</h1>
    <button @click="toggleTrigger('buttonsTrigger')">Open Popup</button>
    <Popup v-if="triggers.buttonsTrigger" @close="toggleTrigger('buttonsTrigger')">
      <h2>Buttons Popup</h2>
      <p>Lorem ipsum dolor sit, amet consectetur adipisicing elit. Blanditiis architecto fuga quam?</p>
    </Popup>
    <Popup v-if="triggers.timedTrigger" @close="toggleTrigger('timedTrigger')">
      <h2>Timed Popup</h2>
      <p>Lorem ipsum dolor sit, amet consectetur adipisicing elit. Fuga, non!</p>
    </Popup>
  </main>
</template>

<style scoped lang="scss">
main{
  display: flex;
  justify-content: center;
  align-items: flex-start;
  flex-direction: column;
  height: 100vh;
}
</style>
