<template>
  <article class="card">
    <div class="card__main row">
      <div class="card__sec" v-for="(item) in data" :key="item.ID">
        <a :href="item.Url" target="_blank" v-if="item.Url">
          <CardItem :item="item" />
        </a>
        <CardItem :item="item" v-else />
      </div>
    </div>
  </article>
</template>

<script>
import CardItem from './CardItem.vue';

export default {
  name: 'Card',
  components: {
    CardItem,
  },
  props: {
    data: Array,
  },
};
</script>

<style scoped>
.row {
  margin-left: -15px;
  margin-right: -15px;
  margin-top: -15px;
}

.card__main {
  display: flex;
  flex-wrap: wrap;
}

.card__sec {
  box-sizing: border-box;
  width: 50%;
  padding: 15px;
}

@media screen and (max-width: 414px) {
  .card__sec {
    width: 100%;
  }
}
</style>
