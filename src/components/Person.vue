<template>
	<div class="person chinese l-flex">
    <p class="content">
      <span v-if="!calendar.contributor">“</span>{{ calendar.content }}<span v-if="!calendar.contributor">”</span>
      <span v-if="calendar.contributor" class="contributor">—— ID：{{ calendar.contributor }}</span>
    </p>
  </div>
</template>

<script>
export default {
  name: 'Person',
  props: {
  	calendar: {
      type: Object
    }
  }
};
</script>

<style scoped>
	.person {
    width: 9rem;
    min-height: 2.666667rem;
    margin: 0.773333rem auto;
    vertical-align: middle;
    align-items: center;
  }
  .person p {
    margin: 0.25rem 0;
    line-height: 140%;
    font-size: 16px;
  }
  [data-dpr="2"] .person .content {
    font-size: 32px;
  }
  [data-dpr="3"] .person .content {
    font-size: 48px;
  }
  .contributor {
    font-size: 12px;
    color: #b2b2b2;
  }
  [data-dpr="2"] .person .contributor {
    font-size: 24px;
  }
  [data-dpr="3"] .person .contributor {
    font-size: 36px;
  }
  
</style>
