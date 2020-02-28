<template>
  <div id="app">
    <search-form/>
    <articles-display :articles='articles'/>
  </div>
</template>

<script>
import SearchForm from './components/SearchForm.vue';
import ArticlesDisplay from './components/ArticlesDisplay.vue';
import {eventBus} from './main.js';

export default {
  name: 'App',
  components: {
    'search-form': SearchForm,
    'articles-display': ArticlesDisplay

  },
  data() {
    return {
      articles: [],
      searchString: ""
    }
  },
  mounted() {
    eventBus.$on('search-string', (searchString) => {
    this.searchString = searchString;
    fetch(`https://content.guardianapis.com/search?q=search&format=json&api-key=test`)
  .then(res => res.json())
  .then(data => this.articles = data.response.results)
  })
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
