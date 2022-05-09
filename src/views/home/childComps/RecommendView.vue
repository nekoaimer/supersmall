<template>
  <div class="recommend">
    <div class="recommend-item" v-for="item in recommends.list">
      <a :href="item.link">
        <img :src="item.image" alt="">
        <div>{{ item.title }}</div>
      </a>
    </div>
  </div>
</template>

<script>
export default {
  name: "RecommendView",
  props: {
    recommends: {
      type: Object,
      default() {
        return {}
      }
    },
  }
}
</script>

<style scoped>
.recommend{
  display: flex;
  width: 100%;
  justify-content: space-around;
  text-align: center;
  padding: 10px 0;
  border-bottom: 8px solid #eee;
}
.recommend-item{
  text-align: center;
}

.recommend-item a {
  display: flex;
  flex-wrap: wrap;
  align-content: space-between;
  justify-content: center;
  font-size: calc(5vw);
}
.recommend-item a img {
  max-width: 80%;
  margin-bottom: 8px;
}
</style>
