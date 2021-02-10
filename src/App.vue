<template>
  <div id="app">
    <Counter />
  </div>
</template>

<script>
import Counter from './components/Counter'
export default {
  name: 'App',
  components: {
    Counter
  }
}
</script>

<style>
:root {
  --primary-color: #474d8a;
  --secondary-color: #3e99d5;
  --support-color: #1e3c91;
  --action-color: #ef7a23;
  --alert-color: #bd3a18;
  --text-color: #f4f4f4;
}

body {
  background-color: var(--primary-color);
  color: var(--text-color);
}
</style>
