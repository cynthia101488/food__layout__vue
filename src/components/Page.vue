<template>
  <div class="page">
    <div class="page__info">{{ `美食頁次 ${switchIndex + 1} / ${dataLen}` }}</div>
    <div class="page__body">
      <button class="page__btn" :class="{ 'js-page__btn': switchIndex === index }"
        type="button"  @click="changePage(index)"
        v-for="(item, index) in dataLen" :key="index">{{ index + 1 }}</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Page',
  props: {
    dataLen: Number,
    switchIndex: Number,
  },
  // data() {
  //   return {
  //     currentIndex: 0,
  //   };
  // },
  methods: {
    changePage(index) {
      this.$emit('changePage', index);
    },
  },
};
</script>

<style scoped>
.page {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.page__btn {
  height: 30px;
  padding-left: 12px;
  padding-right: 12px;
  font-size: 15px;
  color: #999;
  border: none;
  background-color: #ddd;
  cursor: pointer;
}

.page__btn + .page__btn {
  margin-left: 5px;
}

.js-page__btn {
  color: #fff;
  background-color: #0ea4d6;
}

@media screen and (max-width: 414px) {
  .page__info {
    display: none;
  }

  .page__btn {
    margin: 5px;
  }
}
</style>
