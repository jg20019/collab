<script setup>
import { reactive, computed } from 'vue'

const props = defineProps({
  x: Number,
  y: Number
})

const state = reactive({
  contents: 'Happy Hacking!',
  top:  props.y,
  left: props.x,
  clientX: null,
  clientY: null, 
  dX: 0,
  dY: 0,
  el: null,
})

const position = computed(() => {
  return { top: `${state.top}px`, left: `${state.left}px` }
})

const dragNote = (event) => {
  event.preventDefault()
  state.dX = state.clientX - event.clientX
  state.dY = state.clientY - event.clientY

  state.clientX = event.clientX
  state.clientY = event.clientY

  state.top = state.el.offsetTop - state.dY
  state.left = state.el.offsetLeft - state.dX
}

const releaseNote = (event) => {
  document.onmousemove = state.onmousemove
  document.onmouseup   = state.onmouseup
}

const grabNote = (event) => {
  state.clientX = event.clientX
  state.clientY = event.clientY
  state.dragging = true
 
  state.el = event.currentTarget
  document.onmousemove = dragNote
  document.onmouesup = releaseNote
}
</script>

<template>
  <div
    class="note-container" 
    @mousedown="grabNote"
    @mouseup="releaseNote"
    :style="position">
    <textarea
      v-model="state.contents"
      @click="(e) => e.stopPropagation()"
      spellcheck=false
      rows="10" 
      >
    </textarea>
  </div>
</template>

<style>
    div.note-container {
      display: inline-block;
      position: absolute;
      border-radius: 5px;
      border: 10px solid lightgreen;
    }

    div.note-container:hover {
      cursor: pointer;
    }

    textarea {
      width: 95%;
      height: 95%;
      padding: 5px;
      outline: none;
      border: none;
      z-index: 100;
    }

    textarea:focus {
      outline: none;
      border-color: green;
    }

</style>
