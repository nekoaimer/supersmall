<template>
  <div id="app">
    <keep-alive exclude="Detail"><router-view /></keep-alive>
    <MainTabBar></MainTabBar>
  </div>
</template>

<script>
import MainTabBar from "@/components/content/mainTabbar/MainTabBar";
import Home from "./views/home/Home";
export default {
  name: "App",
  components: {
    MainTabBar,
    Home,
  },
};
</script>

<style>
@import "assets/css/base.css";
#app {
  /*width: 100vw;*/
  /*height: 100vh;*/
}
</style>


