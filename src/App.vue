<template>
<div class="container">
  <Calendar />
</div>
</template>

<script>

import Calendar from './components/Calendar';

export default {
  name: 'App',
  components: {
    Calendar
  }
}
</script>

<style>
.container {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
  font-size: 20px;
}
</style>
