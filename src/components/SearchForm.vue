<template lang="html">
  <div class="search-form">
    <label for="search-input">Search Guardian Articles</label>
    <input type="text" name="search-input" v-model="searchString"/>
    <select class="sections-list" name="sections-list" v-model="selectedSection" @change="handleSelect">
      <option v-for="section in sections" :value="section.id">{{section.webTitle}}</option>
    </select>
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
      selectedSection: ""
    }
  },
  props: ['sections'],
  methods: {
    handleSearch: function () {
      eventBus.$emit('search-string', this.searchString)
    },
    handleSelect: function () {
      eventBus.$emit('section-select', this.selectedSection)
    }
  }
}
</script>

<style lang="css" scoped>

.search-form {
  background-color: #052962;
  height: 100px;
  display: flex;
  align-content: center;
  justify-content: center;
}
label {
  color: white;
  margin: auto 0
}

select {
  margin:auto 5px ;
}

button {
  height: 50px;
  height: 30px;
  margin: auto 0px;
}
input {
  width: 40%;
  height: 20px;
  margin: auto 10px
}
</style>
