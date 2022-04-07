<script setup>

import { reactive, computed } from 'vue'

const state = reactive({
  contents: 'Happy Hacking!',
  top:  25,
  left: 25,
  clientX: null,
  clientY: null, 
  movementX: 0,
  movementY: 0,
  onmousemove: null,
  onmouseup: null,
  dragging: false
})


const position = computed(() => {
  return { top: `${state.top}px`, left: `${state.left}px` }
})

const handleDrag = (event) => {
  event.preventDefault()
  state.movementX = state.clientX - event.clientX
  state.movementY = state.clientY - event.clientY

  state.clientX = event.clientX
  state.clientY = event.clientY

  state.top = state.top - state.movementY
  state.left = state.left - state.movementX
}

const handleMouseUp = (event) => {
  if (state.dragging) {
    document.onmousemove = state.onmousemove
    document.onmouseup   = state.onmouseup
  }
}

const handleMouseDown = (event) => {
  event.preventDefault()

  state.clientX = event.clientX
  state.clientY = event.clientY
  state.dragging = true
  
  // Remember these so that we can reset them later
  state.onmousemove = document.onmousemove
  state.onmouseup = document.onmouseup

  document.onmousemove = handleDrag
  document.onmouesup = handleMouseUp
}
</script>

<template>
  <div
    class="note-container" 
    @mousedown="handleMouseUp"
    @mouseup="handleMouseDown"
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
      border-radius: 5px;
    }

    div.note-container:hover {
      cursor: pointer;
    }

    textarea {
      width: 100%;
      height: 100%;
      padding: 5px;
      outline: none;
      border: none;
    }

    textarea:focus {
      outline: none;
      border-color: green;
    }

</style>
