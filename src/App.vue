<template>
  <div id="app">
    <MainTabBar></MainTabBar>
    <router-link to="/home">home</router-link>
    <router-link to="/cart">cart</router-link>
    <router-link to="/category">category</router-link>
    <router-link to="/profile">profile</router-link>
    <keep-alive><router-view> </router-view></keep-alive>
  </div>
</template>

<script>
import MainTabBar from "components/content/mainTabar/MainTabBar";

export default {
  name: 'App',
  components: {
    MainTabBar
  }
}
</script>

<style>
@import "assets/css/base.css";
</style>
