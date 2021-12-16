<template>
  <div class="nav__body">
    <span class="nav__tit">檢視模式：</span>
    <div class="nav__footer">
      <button class="nav__btn" :class="{ 'js-nav__btn': this.$parent.mode === 1 }"
        @click="changeMode(1)">
        <i class="fas fa-th-list"></i>
      </button>
      <button class="nav__btn" :class="{ 'js-nav__btn': this.$parent.mode === 2 }"
        @click="changeMode(2)">
        <i class="fas fa-align-justify"></i>
      </button>
      <button class="nav__btn" :class="{ 'js-nav__btn': this.$parent.mode === 3 }"
        @click="changeMode(3)">
        <i class="fas fa-th-large"></i>
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ModeSelect',
  methods: {
    changeMode(index) {
      this.$emit('changeMode', index);
    },
  },
};
</script>

<style scoped>
.nav__btn {
  margin-left: 5px;
  margin-right: 5px;
  padding: 0;
  font-size: 20px;
  color: #666;
  border: none;
  cursor: pointer;
}

.js-nav__btn {
  color: #000;
}
</style>
