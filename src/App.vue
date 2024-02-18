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
    <Popup
     v-if="triggers.buttonsTrigger"
     :toggleTrigger="toggleTrigger('buttonsTrigger')"
     >
      <h2>My Popup</h2>
    </Popup>
    <Popup v-if="triggers.timedTrigger">
      <h2>My Popup</h2>
    </Popup>
  </main>
</template>

<style scoped lang="scss">

</style>
