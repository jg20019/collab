<script setup>
import Note from './Note.vue'
import Menu from './Menu.vue'

import { computed, reactive } from 'vue';

const state = reactive({
  menu: { 
    top: 200,
    left: 250,
    isVisible: false
  }
})


const menuTop  = computed(() => state.menu.top)
const menuLeft = computed(() => state.menu.left)
const menuIsVisible = computed(() => state.menu.isVisible)

const showContextMenu = (e) => {
  state.menu.top  = e.clientY;
  state.menu.left = e.clientX;
  state.menu.isVisible = !state.menu.isVisible;
};

</script>

<template>
  <div class="background" @click="showContextMenu">
    <Note />
    <Menu v-if="menuIsVisible" :top="menuTop" :left="menuLeft"/>
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
