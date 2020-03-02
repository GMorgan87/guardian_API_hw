<template lang="html">
  <div class="article-list" v-if="this.articles">
    <div class="article-item" v-for="article in this.articles">
      <p>{{article.sectionName}}</p>
      <a  :href="article.webUrl">{{article.webTitle}}</a>
    </div>

  </div>

</template>

<script>
export default {
  props: ['articles']
}
</script>

<style lang="css" scoped>

.article-item {
  width: 15%;
  height: auto;
  padding: 20px;
  background-color: #052962;
  font-weight: bold;
  margin: 5px
}

.article-list {
  width: 95%;
  display: flex;
  flex-wrap: wrap
}

a {
  font-size: 1.2em;
  width: 100%;
  text-align: left;
  text-decoration: none;
  margin: 5px;
  color: white;
}

p {
  color: red;
  font-size: 1.25em;
  margin: 0 0 5px 0;
}

</style>
