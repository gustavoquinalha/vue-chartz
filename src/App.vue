<template>
<div id="app">
  <transition name="fade">
    <router-view></router-view>
  </transition>

</div>
</template>

<script>

export default {
  name: 'app',
  components: {
  }
}
</script>

<style>
  @import 'assets/css/main.scss';
  @import '../node_modules/the-grid-flexbox/css/the-grid.min.css';
</style>
