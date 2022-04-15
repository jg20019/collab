<script setup>
import Note from './Note.vue'
import Menu from './Menu.vue'

import { computed, reactive } from 'vue';

const state = reactive({
  menu: { 
    top: 200,
    left: 250,
    isVisible: false
  },
  notes: [
    {x: 25, y: 25}
  ]
})

const menuTop  = computed(() => state.menu.top)
const menuLeft = computed(() => state.menu.left)
const menuIsVisible = computed(() => state.menu.isVisible)

const showContextMenu = (e) => {
  state.menu.top  = e.clientY
  state.menu.left = e.clientX
  state.menu.isVisible = true
};

const addNote = ({x, y}) => {
  state.notes.push({x, y})
}
const closeMenu = () => {
  state.menu.isVisible = false
}

</script>

<template>
  <div class="background" @click="showContextMenu">
    <Note v-for="({x, y}) in state.notes" :x="x" :y="y" />
    <Menu
      @addNote="addNote"
      @closeMenu="closeMenu"
      v-if="menuIsVisible" :top="menuTop" :left="menuLeft"/>
  </div>
</template>

<style scoped>
  .background {
    position: absolute;
    width: 100%;
    height: 100%;
    top: 0;
    left: 0;
  }
</style>
