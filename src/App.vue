<template>
  <div id="app">
    <search-form :sections='sections'/>
    <articles-display :articles='articles' />
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
      searchString: "",
      sections: [],
      selectedSection: ""
    }
  },
  mounted() {
    eventBus.$on('search-string', (searchString) => {
    this.searchString = searchString;
    if (this.selectedSection) {
      fetch(`https://content.guardianapis.com/search?section=${this.selectedSection}&order-by=newest&page-size=20&q=${searchString}&format=json&api-key=d5bc564c-0e84-4650-a284-ed696ea2ac2d`)
      .then(res => res.json())
      .then(data => this.articles = data.response.results)
    } else {
      fetch(`https://content.guardianapis.com/search?order-by=newest&page-size=20&q=${searchString}&format=json&api-key=d5bc564c-0e84-4650-a284-ed696ea2ac2d`)
      .then(res => res.json())
      .then(data => this.articles = data.response.results)
}
  })

  fetch(`https://content.guardianapis.com/sections?api-key=d5bc564c-0e84-4650-a284-ed696ea2ac2d`)
    .then(res => res.json())
    .then(data => this.sections = data.response.results)

    eventBus.$on('section-select', (selectedSection) => this.selectedSection = selectedSection)
  }
}
</script>

<style>
#app {
  font-family: Georgia, serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center; */
  color: #2c3e50;
}
</style>
