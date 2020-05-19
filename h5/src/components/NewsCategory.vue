<template>
  <div class="row">
    <div class="item" v-for="item in list" :key="item.id">
      <span>{{item.text}}</span>
    </div>
  </div>
</template>
<style scoped>
  .row {
    display: flex;
  }
  .row .item {
    width: 25%;
  }
</style>
<script>
  export default {
    name: "NewsCategory",
    props: {
      list: {
        type: Array,
        default: () => []
      }
    },
    mounted: function() { },
    methods: {
      
    }
  };
</script>
