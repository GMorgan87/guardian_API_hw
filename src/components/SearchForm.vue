<template lang="html">
  <div class="search-form">
    <label for="search-input">Search for articles:</label>
    <input type="text" name="search-input" v-model="searchString"/>
    <button type="button" name="searchbutton" @click="handleSearch">Search</button>
  </div>

</template>

<script>
import {eventBus} from '../main.js';

export default {
  name: 'search-form',
  data(){
    return {
      searchString: "",
    }
  },
  methods: {
    handleSearch: function () {
      eventBus.$emit('search-string', this.searchString)
    }

  }
}
</script>

<style lang="css" scoped>
</style>
