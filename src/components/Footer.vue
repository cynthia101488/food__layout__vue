<template>
  <footer class="footer">
    <div class="footer__sec container mx-auto">
      <p class="footer__tit"> CMoney 全曜財經資訊</p>
      <div class="footer__desc">
        <span class="footer__info">資料來源：</span>
        <a href="https://data.coa.gov.tw/Service/OpenData/ODwsv/ODwsvTravelFood.aspx">政府資料開放平台</a>
      </div>
    </div>
  </footer>
</template>

<script>
export default {
  name: 'Footer',
};
</script>

<style scoped>
.footer {
  background-color: #999;
}

.footer__sec {
  padding: 15px;
}

.footer__tit {
  margin: 0;
  font-size: 18px;
  font-weight: 900;
  color: #ccc;
}

.footer__desc {
  font-size: 14px;
  color: #ccc;
}

.footer__desc a {
  color: #fff;
  text-decoration: none;
}

@media screen and (max-width: 414px) {
  .footer {
    text-align: center;
  }
}
</style>
