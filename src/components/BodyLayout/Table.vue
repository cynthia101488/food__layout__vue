<template>
  <article class="table">
    <table class="table__sec">
      <thead class="table__head">
        <tr class="table__ls">
          <th class="table__tit table-col1">編號</th>
          <th class="table__tit table-col2">行政區域</th>
          <th class="table__tit table-col3">鄉鎮區</th>
          <th class="table__tit table-col4">商家</th>
          <th class="table__tit table-col5">地址</th>
        </tr>
      </thead>
      <tbody class="table__body">
        <tr class="table__ls" v-for="(item, index) in data" :key="item.ID"
          :class="{ 'js-table__ls': index % 2 === 0 ? false : true }">
          <td class="table__item text-right text-gray">{{ startNum + index }}</td>
          <td class="table__item text-gray">{{ item.City }}</td>
          <td class="table__item text-gray">{{ item.Town }}</td>
          <td class="table__item" v-if="item.Url">
            <a :href="item.Url" target="_blank">{{ item.Name }}</a>
          </td>
          <td class="table__item" v-else>{{ item.Name }}</td>
          <td class="table__item">
            <div class="table__desc">
              <p class="table__info text-overflow">{{ item.Address }}</p>
              <p class="table__hidden">{{ item.Address }}</p>
            </div>
          </td>
        </tr>
      </tbody>
    </table>
  </article>
</template>

<script>
export default {
  name: 'Table',
  props: {
    data: Array,
    startNum: Number,
  },
};
</script>

<style scoped>
.table {
  margin-bottom: 15px;
}

.table__sec {
  width: 100%;
  table-layout: fixed;
  border-collapse: collapse;
}

.table__ls {
  background-color: #fff;
}

.table__ls:hover {
  background-color: #eff4f7;
}

.js-table__ls {
  background-color: #f9f9f9;
}

.table__tit, .table__item {
  box-sizing: border-box;
  padding: 15px;
  border: 1px solid #ddd;
}

.table__tit {
  color: #707070;
  border-bottom: 2px solid #ccc;
  background: linear-gradient(to bottom, #f7f7f7, #eee);
}

.table__item a {
  color: #3E99C8;
}

.table__desc {
  position: relative;
}

.table__info, .table__hidden {
  margin: 0;
}

.table__desc:hover .table__hidden{
  display: block;
}

.table__hidden {
  position: absolute;
  top: 24px;
  left: 24px;
  display: none;
  padding: 2px;
  font-size: 12px;
  white-space: nowrap;
  border: 1px solid #666;
  border-radius: 3px;
  background: linear-gradient(to bottom, #fff, #eee);
  box-shadow: 2px 2px 2px rgba(0, 0, 0, .5);
}

.table-col1 {
  width: 65px;
}

.table-col2 {
  width: 95px;
}

.table-col3 {
  width: 95px;
}

.table-col4 {
  width: 265px;
}

.table-col5 {
  width: 370px;
}

.text-right {
  text-align: right;
}

.text-gray {
  color: #666;
}

.text-overflow {
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;
}

@media screen and (max-width: 414px) {
  .table {
    overflow: auto;
  }
}
</style>
