<script setup>
import Note from './Note.vue'
import Menu from './Menu.vue'

import { computed, reactive } from 'vue';

const state = reactive({
  menu: { 
    top: 200,
    left: 250,
    isVisible: true
  }
})


const menuTop  = computed(() => state.menu.top)
const menuLeft = computed(() => state.menu.left)
const menuIsVisible = computed(() => state.menu.isVisible)

</script>

<template>
  <Note />
  <Menu v-if="menuIsVisible" :top="menuTop" :left="menuLeft"/>
</template>

<style scoped>
</style>
