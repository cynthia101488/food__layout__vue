<template>
  <div class="card__content">
    <div class="img__inner">
      <img class="image" :src="item.PicURL" :alt="item.Name" loading="lazy">
    </div>
    <div class="card__info">
      <div class="card__head">
        <h3 class="card__tag">{{ item.City }}</h3>
        <h4 class="card__name">{{ item.Town }}</h4>
      </div>
      <div class="card__body">
        <h2 class="card__tit">{{ item.Name }}</h2>
      </div>
      <div class="card__footer">
        <p class="card__desc">{{ item.HostWords }}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CardItem',
  props: {
    item: Object,
  },
};
</script>

<style scoped>
.card__content {
  position: relative;
  overflow: hidden;
}

.card__content .img__inner {
  position: relative;
  height: 200px;
  overflow: hidden;
}

.card__content .img__inner::before {
  content: "";
  position: absolute;
  z-index: 1;
  display: block;
  width: 100%;
  height: 100%;
  background: linear-gradient(to bottom, rgba(0, 0, 0, 0), rgba(0, 0, 0, .5));
}

.card__content img {
  transition: transform 1s;
}

.card__content:hover img {
  transform: scale(1.3);
}

.card__info {
  position: absolute;
  bottom: 0;
  z-index: 2;
  padding: 10px;
  transform: translateY(70px);
  transition: transform 1s;
}

.card__content:hover .card__info {
  transform: translateY(0);
}

.card__head {
  display: flex;
  align-items: center;
  margin-bottom: 2px;
}

.card__tag, .card__name, .card__tit {
  margin: 0;
  font-weight: 400;
  color: #fff;
}

.card__tag {
  margin-right: 5px;
  padding: 2px;
  font-size: 14px;
  color: #fff;
  background-color: #0ea4d6;
}

.card__name {
  font-size: 14px;
  font-style: italic;
}

.card__tit {
  font-size: 16px;
  font-weight: 900;
}

.card__desc {
  height: 4.5em;
  margin: 0;
  font-size: 15px;
  line-height: 1.5em;
  color: #fff;
  overflow: hidden;
}

.card__desc::before {
  content: "";
  display: block;
  width: 50px;
  height: 3px;
  margin-top: 10px;
  margin-bottom: 10px;
  background-color: #fff;
}
</style>
