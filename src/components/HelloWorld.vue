<script setup>
import { reactive } from 'vue'

const state = reactive({contents: ""})

function save() {
  localStorage.setItem('editor', state.contents)
}

function load() {
  state.contents = localStorage.getItem('editor') || 'Happy Hacking!'
}

load()

</script>

<template>
  <button id="save" @click="save"> save </button>
  <textarea v-model="state.contents" spellcheck=false rows="10"></textarea>
</template>

<style scoped>

#save {
  position: absolute;
  top: 20px;
  right: 20px;
  padding: 10px;
  background-color: lightgreen;
  outline: none;
  border: none;
  border-radius: 5px;
}

#save:hover {
  background-color: green;
  color: white;
}

textarea {
  padding: 10px;
  border: 10px solid lightgreen;
  display: inline-block;
  padding: 10px;
  position: relative;
  top: 50%;
  left: 50%;
}

textarea:focus {
  outline: none;
  border-color: green;
}
</style>
