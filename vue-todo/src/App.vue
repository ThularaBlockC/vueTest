<script setup>
import { RouterView } from 'vue-router'
import StickyHeader from './components/StickyHeader.vue';
</script>

<template>
  <StickyHeader/>
  <RouterView />
</template>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Ubuntu:wght@400;500;600;700;800;900&display=swap');

* {
  font-family: "Ubuntu", sans-serif;
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.container {
  max-width: 1100px;
  margin: 0 auto;
}
</style>
