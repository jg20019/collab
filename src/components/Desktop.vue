<script setup>
import Note from './Note.vue'

</script>

<template>
  <button id="save" @click="save"> save </button>
  <Note />
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
</style>
