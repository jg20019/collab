<script setup>

import { computed } from 'vue';

const emit = defineEmits(['closeMenu', 'addNote'])
const props = defineProps(['top', 'left'])

const styleObject = computed(() => {
  return {
    top: `${props.top}px`,
    left: `${props.left}px`
  }
});


const emitAddNote = (e) => {
  e.stopPropagation()
  emit('closeMenu')
  emit('addNote', {x: e.clientX, y: e.clientY})
}

const emitCloseNote = (e) => {
  e.stopPropagation()
  emit('closeMenu')
}


</script>

<template>
  <div 
    class="menu-container"
    :style="styleObject">
    <button @click="emitCloseNote"> close </button>
    <button @click="emitAddNote"> add note </button>
    <button> save </button>
  </div>
</template>

<style scoped>
.menu-container {
  border-radius: 5px;
  border: 1px solid lightgreen;
  display: flex;
  flex-direction: column;
  width: 100px;
  position: absolute;
}

.menu-container button {
  background-color: lightgreen;
  outline: none;
  border: none;
  padding-bottom: 1px;
}

</style>
