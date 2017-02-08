<template>
<div id="app" class="app">
  <template v-if="loaded">
    <header class="header">
      <Today :calendar="calendar" :today="today"></Today>
    </header>
    <Detailed :calendar="calendar" :today="today"></Detailed>
    <Person :calendar="calendar"></Person>
    <Movie :calendar="calendar"></Movie>
  </template>
</div>
</template>

<script>
import Today from './components/Today';
import Detailed from './components/Detailed';
import Person from './components/Person';
import Movie from './components/Movie';
import axios from 'axios';
import config from './config';

export default {
  name: 'app',
  data: function () {
    return {
      today: config.APP_DATA.today,
      loaded: false,
      calendar: {}
    };
  },
  computed: {
    year: function () {
      return this.$data.today.getFullYear();
    },
    month: function () {
      return this.$data.today.getMonth() + 1;
    },
    date: function () {
      return this.$data.today.getDate();
    }
  },
  components: {
    Today,
    Detailed,
    Person,
    Movie,
  },
  methods: {
    init: function () {
      const vm = this;
      axios.get(config.APP_DATA.api, {
        params: {
          year: this.year,
          month: this.month,
          date: this.date
        }
      })
      .then(function (response) {
        if (response.data !== undefined && response.data.date !== undefined) {
          this.$data.calendar = response.data; 
          this.$data.loaded = true;
        }
      }.bind(this))
      .catch(function (error) {
        alert('抱歉发生错误');
        console.error(error);
      });
    }
  },
  created: function () {
    this.init();
  }
};
</script>

<style>
@font-face {
  font-family: 'DietDidotExtra';
  src: url('../static/font/DietDidotExtra.eot?#font-spider') format('embedded-opentype'),
       url('../static/font/DietDidotExtra.woff2') format('woff2'),
       url('../static/font/DietDidotExtra.woff') format('woff'),
       url('../static/font/DietDidotExtra.ttf') format('truetype'),
       url('../static/font/DietDidotExtra.svg') format('svg');
  font-weight: normal;
  font-style: normal;
}
.l-flex {
  display: flex;
}
.header {
  padding-top: 1rem;
}
.chinese {
  font-family: PingFang SC, "Helvetica Neue", Helvetica, 'Hiragino Sans GB', 'Microsoft YaHei', 'WenQuanYi Micro Hei', Arial,sans-serif;
}
</style>
