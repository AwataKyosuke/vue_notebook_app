<template>
  <div class="item">
    <p class="item-title">
      <router-link :to="{name: 'Article', params: { id: article.id }}">{{ article.title }}</router-link>
    </p>
    <p class="item-detail">
      <font-awesome-icon :icon="['fas', 'calendar-alt']" class="item-date-icon" />
      <span class="item-date">{{ article.date }}</span>

      <font-awesome-icon :icon="['fas', 'folder-open']" class="item-categories-icon" />
      <span class="item-categories" v-for="category in article.categoryId" :key="category.id">{{ getCategoryName(category) }}</span>

      <font-awesome-icon :icon="['fas', 'tags']" class="item-tags-icon" />
      <span class="item-tags" v-for="tag in article.tagId" :key="tag.id">{{ getTagName(tag) }}</span></p>
    </div>
</template>

<script>
export default {
  name: 'Item',

  props: [ 'article' ],

  methods:{
    getTagName(tagId){
      return this.$store.state.tags.filter((x => x.id === tagId))[0].name + ' / '
    },

    getCategoryName(categoryId){
      return this.$store.state.categories.filter((x => x.id === categoryId))[0].name + ' / '
    }
  }
}
</script>

<style scoped>

.item {
  border-bottom: 0.5px solid #e9eaea;
  padding-top: 1.5vh;
  margin: 0 0 0.5vh 0;
}

.item-title {
  padding: 0;
  margin: 0;
  font-weight: bold;
  font-size: 0.9vw;
}

.item-detail {
  margin: 0.5vh 0 0.5vh 0;
}

.item-title a {
  color: black;
  text-decoration: none;
}

.item-date {
  color: darkgrey;
  font-size: 0.8vw;
}

.item-date-icon {
  padding: 0 5px 1.1px 0;
  color: darkgray;
  font-size: 0.8vw;
}

.item-categories {
  color: darkgray;
  font-size: 0.8vw;
}

.item-categories-icon {
  padding: 0 5px 0px 0;
  color: darkgray;
  margin-left: 1vw;
  font-size: 0.8vw;
}

.item-tags {
  color: darkgray;
  font-size: 0.8vw;
}

.item-tags-icon {
  padding: 0 5px 0px 0;
  color: darkgray;
  margin-left: 1vw;
  font-size: 0.8vw;
}

</style>
