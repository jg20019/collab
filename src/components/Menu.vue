<script setup>

import { computed, defineProps } from 'vue';

const props = defineProps(['top', 'left'])

const styleObject = computed(() => {
  return {
    top: `${props.top}px`,
    left: `${props.left}px`
  }
});

</script>

<template>
  <div 
    class="menu-container"
    :style="styleObject">
    <button> close </button>
    <button> add note </button>
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
