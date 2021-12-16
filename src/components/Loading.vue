<template>
  <div class="loading" :class="{ 'js-hide' : isLoad}">
    <div class="loading__body">
      <img src="https://illinoislock.com/assets/images/loading.gif" alt="loading...">
      <p class="loading__text">資料下載中...請稍後！</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Loading',
  props: {
    isLoad: Boolean,
  },
};
</script>

<style scoped>
.loading {
  position: absolute;
  width: 100%;
  height: 100%;
  top: 0;
  background-color: rgba(0,0,0,.7);
}

.loading__body {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}

.loading__body img {
  width: 80px;
  margin-left: 20px;
}

.loading__text {
  font-size: 12px;
  color: #fff;
}

.js-hide {
  display: none;
}
</style>
