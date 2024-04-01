
<template>
  <div id="app">
    <AppHeader/>
    <div class="container-fluid mt-3">
      <router-view/>
    </div>
  </div>
</template>

<script>
import AppHeader from '../src/components/AppHeader.vue';
export default {
  components: {
    AppHeader,
  },
} 
</script>

<style>

</style>