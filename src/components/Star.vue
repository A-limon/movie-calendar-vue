<template>
  <div :class="['star', ratingStyle]"></div>
</template>

<script>
export default {
  name: 'Star',
  props: {
    rating: {
      type: Number,
      required: true
    }
  },
  computed: {
    ratingStyle: function () {
      return 'bigstar' + Math.ceil(this.rating);
    }
  },
}
</script>

<style scoped>
  .star {
    width: 1.0rem;
    height: 0.199rem;
    overflow: hidden;
    background: url('../../static/rating.png');
    background-size: cover;
  }
  .bigstar10 {
    background-position: 0 0px;
  }
  .bigstar9 {
    background-position: 0 -0.2rem;
  }
  .bigstar8 {
    background-position: 0 -0.4rem;
  }
  .bigstar7 {
    background-position: 0 -0.6rem;
  }
  .bigstar6 {
    background-position: 0 -0.8rem;
  }
  .bigstar5 {
    background-position: 0 -1.0rem;
  }
  .bigstar4 {
    background-position: 0 -1.2rem;
  }
  .bigstar3 {
    background-position: 0 -1.4rem;
  }
  .bigstar2 {
    background-position: 0 -1.6rem;
  }
  .bigstar1 {
    background-position: 0 -1.8rem;
  }
  .bigstar0 {
    background-position: 0 -2.0rem;
  }
</style>
