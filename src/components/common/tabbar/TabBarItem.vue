<template>
  <div @click="tabClick" class="tab-bar-item">
    <div v-if="!isActive">
      <slot name="item-icon"></slot>
    </div>
    <div v-else>
      <slot name="item-icon-active"></slot>
    </div>
    <div :style="isActive?{color:activeColor}:{}">
      <slot name="item-text"></slot>
    </div>
  </div>
</template>

<script>
export default {
  name: "TabBarItem",
  data() {
    return{
      // isActive:true
    }
  },
  props:{
    activeColor:{
      type:String,
      default :'#000'
    },
    path:[String]
  },
  computed:{
    isActive:{
      set(){},
      get(){
        console.log(this.$route)
        // return this.$route.path.indexOf(this.path) !== -1
        return this.$route.path == this.path
      }

    },
  },
  methods: {
    tabClick() {
      this.$router.replace(this.path)
      this.isActive = !this.isActive
    }
  }
}
</script>

<style scoped>
.tab-bar-item {
  flex: 1;
  height: 49px;
  background-color: pink;
  font-size: 12px;
}

.tab-bar-item img {
  width: 24px;
  height: 24px;
  margin-top: 7px;
}
</style>
