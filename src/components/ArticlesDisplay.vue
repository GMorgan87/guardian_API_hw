<template lang="html">
  <div class="article-list">
    <a v-for="article in this.articles" :href="article.webUrl">{{article.webTitle}}</a>
  </div>

</template>

<script>
export default {
  props: ['articles']
}
</script>

<style lang="css" scoped>



</style>
