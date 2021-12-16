<template>
  <div class="list__content">
    <div class="img__inner">
      <img class="image" :src="item.PicURL" :alt="item.Name" loading="lazy">
    </div>
    <div class="list__info">
      <div class="list__head">
        <h2 class="list__tit">{{ item.Name }}</h2>
      </div>
      <div class="list__footer">
        <h3 class="list__tag">{{ item.City }}</h3>
        <h4 class="list__name">{{ item.Town }}</h4>
      </div>
      <div class="list__body">
        <p class="list__desc">{{ textLimit(item.HostWords) }}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ListItem',
  props: {
    item: Object,
  },
  methods: {
    textLimit(text) {
      const len = text.length;
      if (window.innerWidth <= 414) {
        return len > 40 ? `${text.substring(0, 40)}...` : text;
      }
      return len > 100 ? `${text.substring(0, 100)}...` : text;
    },
  },
};
</script>

<style scoped>
.list__content {
  display: flex;
}

.list__content .img__inner {
  position: relative;
  width: 28%;
  margin-right: 30px;
  overflow: hidden;
}

.list__info {
  width: 72%;
}

.list__content .img__inner::before {
  content: "";
  position: absolute;
  display: block;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, .3);
}

.list__content img {
  transition: transform 1s;
}

.list__content:hover img{
  transform: scale(1.3);
}

.list__tit {
  margin: 0;
  font-size: 30px;
  color: #000;
}

.list__footer {
  position: absolute;
  top: 0;
  left: 0;
}

.list__tag {
  position: relative;
  left: -100%;
  margin: 0;
  padding: 3px;
  font-size: 14px;
  font-weight: 400;
  color: #fff;
  background-color: #0ea4d6;
}

.list__name {
  position: relative;
  top: 10px;
  left: -30px;
  width: 16px;
  margin: 0;
  font-weight: 400;
  color: #666;
}

.list__desc {
  font-size: 15px;
  color: #666;
  line-height: 1.6em;
}

@media screen and (max-width: 414px) {
  .list__content {
      display: block;
    }

  .list__content .img__inner {
    width: 100%;
    margin-right: 0;
  }

  .list__info {
    width: 100%;
  }

  .list__tit {
    margin: 0;
    margin-top: 15px;
    font-size: 20px;
  }

  .list__footer {
    position: relative;
    display: flex;
    align-items: center;
    margin-top: 10px;
  }

  .list__tag {
    left: 0;
    margin-right: 10px;
  }

  .list__name {
    top: 0;
    left: 0;
    width: auto;
    font-weight: 900;
  }
}
</style>
