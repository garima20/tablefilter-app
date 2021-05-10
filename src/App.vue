<template>
  <div id="app">
    <FilterTable />
  </div>
</template>

<script>
import FilterTable from './components/FilterTable.vue'

export default {
  name: 'App',
  components: {
    FilterTable
  }
}
</script>

<style>
@import './assets/styles/main.css';
</style>
