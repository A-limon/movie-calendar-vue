<template>
  <div class="date-section">
    <p :class="['date', {'weekend': isWeekend}]">
      {{ date }}
    </p>
    <div :class="['related', {'weekend': isWeekend}]">
      <template v-if="calendar.suggestion !== undefined">
        <p v-if="!calendar.detailed_date">{{ calendar.holiday }}</p>
        <p>{{ calendar.related_information }}</p>
        <p v-if="calendar.detailed_date">{{ calendar.detailed_date }}</p>
      </template>
       <template v-else>
        <p>{{ calendar.related_information }}</p>
        <p class="line">（ {{ calendar.detailed_date }} ）</p>
      </template>
    </div>
    <div :class="['sloar', {'weekend': isWeekend}]" v-if="calendar.sloar_term">
      {{ calendar.sloar_term }}
    </div>
  </div>
</template>

<script>
export default {
  name: 'Detailed',
  props: {
    today: {
      type: Date
    },
    calendar: {
      type: Object
    }
  },
  computed: {
    date: function () {
      return this.today.getDate();
    },
    day: function () {
      const day = this.today.getDay();
      if (day === 0) {
        return 7;
      } else {
        return day;
      }
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
  .date-section {
    width: 7rem;
    margin: 0 auto;
    position: relative;
  }
  .date {
    padding: 0.6rem 0 0.1rem 0;
    text-align: center;
    line-height: 100%;
    font-size: 180px;
    font-family: 'DietDidotExtra';
  }
  .date.weekend {
    color: #529856;
  }
  [data-dpr="2"] .date-section .date {
    font-size: 380px;
  }
  [data-dpr="3"] .date-section .date {
    font-size: 540px;
  }
  .related {
    width: 7rem;
    text-align: center;
    line-height: 160%;
    margin: 0 auto;
    padding: 0 0 0.333333rem 0;
    border-bottom: 1px solid #b2b2b2;
    font-size: 14px;
    font-weight: bold;
  }
  [data-dpr="2"] .related {
    font-size: 28px;
  }
  [data-dpr="3"] .related {
    font-size: 42px;
  }
  .related.weekend {
    color: #529856;
    border-color: #529856;
  }
  .related .line {
    font-size: 12px;
    font-weight: normal;
  }
  [data-dpr="2"] .related .line {
    font-size: 24px;
  }
  [data-dpr="3"] .related .line {
    font-size: 36px;
  }
  .sloar {
    position: absolute;
    top: 50%;
    right: 0;
    width: 0.5rem;
    padding: 0.106667rem 0.066667rem;
    text-align: center;
    font-size: 14px;
    font-weight: bold;
    line-height: 100%;
    border: 1px solid #000;
  }
  [data-dpr="2"] .sloar {
    font-size: 28px;
  }
  [data-dpr="3"] .sloar {
    font-size: 42px;
  }
  .sloar.weekend {
    background: #529856;
    color: #fff;
    border-color: #529856;
  }
</style>
