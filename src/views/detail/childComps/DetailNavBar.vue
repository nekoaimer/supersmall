<template>
  <div>
    <NavBar>
      <div class="back" slot="navbar-left" @click="back">
        <img src="~assets/img/common/back.svg" alt="" />
      </div>
      <div class="title" slot="navbar-center">
        <div
          v-for="(item, i) in titles"
          class="title-item"
          :class="{ active: i == currentIndex }"
          @click="titleClick(i)"
        >
          {{ item }}
        </div>
      </div>
    </NavBar>
  </div>
</template>

<script>
import NavBar from "@/components/common/navbar/NavBar";
export default {
  name: "DetailNavBar",
  components: {
    NavBar,
  },
  data() {
    return {
      titles: ["商品", "参数", "评论", "推荐"],
      currentIndex: 0,
    };
  },
  methods: {
    titleClick(i) {
      this.currentIndex = i;
      console.log(i);
    },
    back() {
      this.$router.back();
    },
  },
};
</script>

<style scoped>
.title {
  display: flex;
  justify-content: space-around;
}
/*.title-item{*/
/*  flex: 1;*/
/*}*/
.active {
  color: #c20c0c;
}
.back img {
  vertical-align: middle;
}
</style>
