<template>
  <div class="nav__select">
    <select class="nav__ls" v-model="computedSelected">
      <option class="nav__item" value="" selected disabled>{{ listCaption }}</option>
      <option class="nav__item" :value="item"
        v-for="(item, index) in list" :key="index">{{ item }}</option>
    </select>
  </div>
</template>

<script>
export default {
  name: 'ZoneSelect',
  props: {
    list: Array,
    listCaption: String,
    current: String,
  },
  computed: {
    computedSelected: {
      get() {
        return this.current;
      },
      set(val) {
        this.$emit('changeOption', val);
      },
    },
  },
};
</script>

<style scoped>
.nav__select {
  position: relative;
}

.nav__select::after {
  content: "";
  position: absolute;
  top: 15px;
  right: 5px;
  border: 4px solid transparent;
  border-top-color: #000;
}

.nav__select + .nav__select {
  margin-left: 10px;
}

.nav__ls {
  box-sizing: border-box;
  width: 160px;
  padding: 10px;
  font-size: 16px;
  border: none;
  border-radius: 5px;
  outline-color: #a3c5fc;
  background-color: #d6d6d6;
  appearance: none;
  cursor: pointer;
}

@media screen and (max-width: 414px) {
  .nav__select {
    margin-bottom: 15px;
  }

  .nav__ls {
    width: 100%;
  }

  .nav__select + .nav__select {
    margin-left: 0;
  }
}
</style>
