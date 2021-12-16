<template>
  <div id="app">
    <header class="header container mx-auto">
      <h1 class="header__tit">農村地方美食小吃特色料理</h1>
    </header>
    <div class="content container mx-auto">
      <main class="main">
        <div class="nav">
          <div class="nav__head">
            <ZoneSelect :list="computedCity" list-caption="請選擇行政區域..."
              :current="currentCity" @changeOption="currentCity = $event" />
            <ZoneSelect :list="computedTown" list-caption="請選擇鄉鎮區..."
              :current="currentTown" @changeOption="currentTown = $event" />
          </div>
          <ModeSelect @changeMode="mode = $event" />
        </div>
        <List :data="computedFilterData[switchIndex]" v-if="mode === 1" />
        <Table :data="computedFilterData[switchIndex]" :startNum="switchIndex * rowSize + 1"
          v-else-if="mode === 2" />
        <Card :data="computedFilterData[switchIndex]" v-else />
        <Page :dataLen="computedFilterData.length" :switchIndex="switchIndex"
          @changePage="switchIndex = $event" />
      </main>
      <Aside />
    </div>
    <Footer />
    <Loading :isLoad="isLoad" />
  </div>
</template>

<script>
import ZoneSelect from '@/components/NavSelect/ZoneSelect.vue';
import ModeSelect from '@/components/NavSelect/ModeSelect.vue';
import List from '@/components/BodyLayout/List.vue';
import Table from '@/components/BodyLayout/Table.vue';
import Card from '@/components/BodyLayout/Card.vue';
import Page from '@/components/Page.vue';
import Aside from '@/components/Aside.vue';
import Footer from '@/components/Footer.vue';
import Loading from '@/components/Loading.vue';

export default {
  name: 'App',
  components: {
    ZoneSelect,
    ModeSelect,
    List,
    Table,
    Card,
    Page,
    Aside,
    Footer,
    Loading,
  },
  data() {
    return {
      data: [],
      currentCity: '',
      currentTown: '',
      switchIndex: 0,
      rowSize: 10,
      mode: 1,
      isLoad: false,
    };
  },
  methods: {
    pageSplit(data) {
      const arr = [];
      for (let i = 0, len = data.length; i < len; i += this.rowSize) {
        arr.push(data.slice(i, i + this.rowSize));
      }
      return arr;
    },
  },
  computed: {
    computedCity() {
      const allPlace = this.data.map((item) => item.City);
      return allPlace.filter((item, index) => allPlace.indexOf(item) === index);
    },
    computedTown() {
      const arr = [];
      this.data.forEach((item) => {
        if (item.City === this.currentCity) {
          arr.push(item);
        }
      });
      const allPlace = arr.map((item) => item.Town);
      return allPlace.filter((item, index) => allPlace.indexOf(item) === index);
    },
    computedFilterData() {
      const cityArr = [];
      const townArr = [];

      if (this.currentCity) {
        this.data.forEach((item) => {
          if (item.City === this.currentCity) {
            cityArr.push(item);
          }
        });
        if (this.currentTown) {
          cityArr.forEach((item) => {
            if (item.Town === this.currentTown) {
              townArr.push(item);
            }
          });
          return this.pageSplit(townArr);
        }
        return this.pageSplit(cityArr);
      }
      return this.pageSplit(this.data);
    },
  },
  watch: {
    currentCity() {
      this.switchIndex = 0;
      this.currentTown = '';
      // this.$nextTick(() => {
      //   this.$refs.page.currentIndex = 0;
      // });
    },
    currentTown() {
      this.switchIndex = 0;
      // this.$nextTick(() => {
      //   this.$refs.page.currentIndex = 0;
      // });
    },
  },
  created() {
    const api = 'https://data.coa.gov.tw/Service/OpenData/ODwsv/ODwsvTravelFood.aspx';
    this.$http.get(api).then((res) => {
      this.data = res.data;
    })
      .finally(() => {
        this.isLoad = true;
      });
  },
};
</script>

<style>
body {
  margin: 0;
  font-family: Arial, Helvetica, "微軟正黑體", sans-serif;
  background-color: #eee;
}

img {
  max-width: 100%;
  width: 100%;
  height: 100%;
  object-fit: cover;
  vertical-align: bottom;
}

.container {
  width: 1200px;
}

.mx-auto {
  margin-left: auto;
  margin-right: auto;
}

.header__tit {
  margin-top: 10px;
  margin-bottom: 35px;
  font-size: 30px;
  text-align: center;
}

.content {
  display: flex;
  margin-bottom: 30px;
}

.main {
  width: 75%;
}

.nav {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 15px;
}

.nav__head, .nav__body {
  display: flex;
}

.nav__tit {
  color: #999;
}

.aside {
  box-sizing: border-box;
  width: 25%;
  padding-left: 30px;
}

@media screen and (max-width: 414px) {
  .container {
    width: 384px;
  }

  .header__tit {
    font-size: 26px;
    margin-bottom: 30px;
  }

  .nav {
    flex-direction: column;
  }

  .nav__head {
    flex-direction: column;
    width: 100%;
  }

  .main {
    width: 100%;
  }

  .aside {
    display: none;
  }
}

@media screen and (max-width: 375px) {
  .container {
    width: 345px;
  }
}

@media screen and (max-width: 360px) {
  .container {
    width: 330px;
  }
}

@media screen and (max-width: 320px) {
  .container {
    width: 290px;
  }

  .header__tit {
    font-size: 24px;
  }
}
</style>
