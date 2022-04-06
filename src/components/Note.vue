<script setup>

import { reactive } from 'vue'

const state = reactive({contents: ""})
state.contents = 'Happy Hacking!'

</script>

<template>
  <textarea
    v-model="state.contents"
    spellcheck=false
    rows="10">
  </textarea>
</template>

<style>
    textarea {
      padding: 10px;
      border: 10px solid lightgreen;
      display: inline-block;
      padding: 10px;
    }

    textarea:focus {
      outline: none;
      border-color: green;
    }
</style>
