<template>
  <aside class="aside">
    <div class="aside__img" v-for="(item, index) in picObj" :key="index"
      :class="{ 'js-aside__img--fix': index === picObj.length - 1 }">
      <img class="image" :src="require(`@/assets/image/${item.src}`)" :alt="item.alt">
    </div>
  </aside>
</template>

<script>
export default {
  name: 'Aside',
  data() {
    return {
      picObj: [
        {
          src: 'adv1.png',
          alt: 'Google Pixel 4',
        },
        {
          src: 'adv2.png',
          alt: '股市阿水-飆股狙擊室',
        },
        {
          src: 'adv3.png',
          alt: '森聯摩天41',
        },

      ],
    };
  },
};
</script>

<style scoped>
.aside__img {
  margin-bottom: 15px;
}

.js-aside__img--fix {
  position: sticky;
  top: 0;
}
</style>
