<template>
  <div id="app">
    <search-form/>
  </div>
</template>

<script>
import SearchForm from './components/SearchForm.vue';
import {eventBus} from './main.js'

export default {
  name: 'App',
  components: {
    'search-form': SearchForm
  },
  data() {
    return {
      articles: [],
      searchString: ""
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
