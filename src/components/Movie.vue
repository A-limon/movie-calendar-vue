<template>
  <div class="movie l-flex" @click="jumpToDouBan">
   <div class="info">
     <p class="movie-title chinese">《{{ calendar.suggestion }}》</p>
     <div class="rate l-flex">
      <div class="rating">{{ calendar.rating }}</div>
      <div class="rating-poing">
        <Star :rating="+calendar.rating"></Star>
        <p class="comments">{{ calendar.number_of_comments }}人在豆瓣评价</p>
      </div>
     </div>
   </div>
   <div class="pic">
     <img :src="pic">
   </div>
  </div>
</template>

<script>
import Star from './Star';
export default {
  name: 'Movie',
  props: {
    calendar: {
      type: Object
    }
  },
  computed: {
    pic: function () {
      return this.calendar.pic ? this.calendar.pic.match(/^(.+)(\?imageView)/)[1] : '';
    }
  },
  methods: {
    jumpToDouBan: function () {
      if (this.calendar.url) {
        setTimeout(function () {
          window.location.href = 'https://movie.douban.com/subject/' + this.calendar.url.replace(/(douban:\/\/douban.com\/movie\/)/,'');
        }.bind(this), 2000);
        window.location = this.calendar.url;
      }
    }
  },
  components: {
    Star
  }
}
</script>

<style scoped>
  .movie {
    width: 8.6rem;
    margin: 0 auto;
    align-items: center;
  }
  .info {
    flex: 4;
  }
  .pic {
    flex: 1;
    text-align: right;
  }
  .pic img {
    height: 1.6rem;
  }
  .movie-title {
    font-size: 18px;
    font-weight: bold;
  }
  [data-dpr="2"] .movie-title {
    font-size: 36px;
  }
  [data-dpr="3"] .movie-title {
    font-size: 54px;
  }
  .rate {
    align-items: center;
  }
  .rate .rating {
    font-size: 32px;
    color: #555450;
  }
  [data-dpr="2"] .rate .rating {
    font-size: 64px;
  }
  [data-dpr="3"] .rate .rating {
    font-size: 96px;
  }
  .rate .rating-poing {
    margin-left: 0.2rem;
  }
  .rate .rating-poing .comments {
    margin-top: 0.05rem;
    font-size: 12px;
    color: #555450;
  }
  [data-dpr="2"] .rate .rating-poing .comments {
    font-size: 24px;
  }
  [data-dpr="3"] .rate .rating-poing .comments {
    font-size: 36px;
  }
</style>
