<script setup>

import { reactive, computed } from 'vue'

const state = reactive({
  contents: 'Happy Hacking!',
  top:  25,
  left: 25,
})

const position = computed(() => {
  return { top: `${state.top}px`, left: `${state.left}px` }
})

</script>

<template>
  <div class="note-container" 
    :style="position">
    <textarea
      v-model="state.contents"
      spellcheck=false
      rows="10" 
      >
    </textarea>
  </div>
</template>

<style>
    div.note-container {
      border: 10px solid lightgreen;
      display: inline-block;
      position: absolute;
    }

    div.note-container:hover {
      cursor: pointer;
    }

    textarea {
      width: 100%;
      height: 100%;
      outline: none;
      border: none;
    }

    textarea:focus {
      outline: none;
      border-color: green;
    }

</style>
