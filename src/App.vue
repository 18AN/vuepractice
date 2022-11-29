<template>
  <div class="app">
    <navbar></navbar>
    <router-view></router-view>
  </div>
</template>

<script>
import Navbar from '@/UI/Navbar.vue';
export default {
  components: { Navbar },

}
</script>

<style>
* {
  margin: 0px;
  padding: 0px;
  box-sizing: border-box;
}

.app {
  padding: 2rem;
}
</style>