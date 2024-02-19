<script setup>
import {ref} from 'vue'
const props = defineProps({
    toggleTrigger:Function
})

const emit = defineEmits(['close'])

const close = () => {
  emit('close')
}
</script>

<template>
    <div class="popup">
        <div class="popup-inner">
            <slot />
            <button @click="close" class="popup-close">Close Popup</button>
        </div>
    </div>
</template>

<style scoped lang="scss">
.popup{
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background-color: rgba(0, 0, 0, 0.6);
    z-index: 9;
    display: flex;
    justify-content: center;
    align-items: center;
    .popup-inner{
        background-color: white;
        padding: 2rem;
    }
}
</style>

