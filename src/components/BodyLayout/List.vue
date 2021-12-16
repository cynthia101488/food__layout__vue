<template>
  <article class="list">
    <div class="list__sec" v-for="(item) in data" :key="item.ID">
      <a :href="item.Url" target="_blank" v-if="item.Url">
        <ListItem :item="item" />
      </a>
      <ListItem :item="item" v-else />
    </div>
  </article>
</template>

<script>
import ListItem from './ListItem.vue';

export default {
  name: 'List',
  components: {
    ListItem,
  },
  props: {
    data: Array,
  },
};
</script>

<style scoped>
.list__sec {
  position: relative;
  box-sizing: border-box;
  margin-bottom: 15px;
  padding: 15px;
  background-color: #fff;
}

.list__sec a {
  text-decoration: none;
}
</style>
