<template>
  <div :class="['today','l-flex',{'weekend': isWeekend}]">
    <span class="month">{{ monthToShow }}月</span>
    <span class="week">星期{{ dayToShow }}</span>
    <span class="lunar">农历{{ calendar.lunar_date }}</span>
  </div>
</template>

<script>
export default {
  name: 'Today',
  props: {
    today: {
      type: Date
    },
    calendar: {
      type: Object
    }
  },
  computed: {
    month: function () {
      return this.today.getMonth() + 1;
    },
    monthToShow: function () {
      const monthChinese = ['一', '二', '三', '四', '五', '六', '七', '八', '九', '十' ,'十一' ,'十二'];
      return monthChinese[this.month - 1];
    },
    day: function () {
      const day = this.today.getDay();
      if (day === 0) {
        return 7;
      } else {
        return day;
      }
    },
    dayToShow: function () {
      const dayChinese = ['一', '二', '三', '四', '五', '六', '日'];
      return dayChinese[this.day - 1];
    },
    isWeekend: function () {
      if (this.day === 6 || this.day ===7) {
        return true;
      } else {
        return false;
      }
    }
  }
};
</script>

<style scoped>
  .today {
    width: 7rem;
    height: 1rem;
    margin: 0 auto;
    border-top: 2px solid #b2b2b2;
    border-bottom: 2px solid #b2b2b2;
    text-align: center;
    justify-content: space-around;
    align-items: center;
    font-size: 16px;
  }
  [data-dpr="2"] .today {
    font-size: 32px;
  }
  [data-dpr="3"] .today {
    font-size: 48px;
  }
  .today.weekend {
    background: #529856;
    color: #fff;
    border-color: #529856;
  }
</style>
