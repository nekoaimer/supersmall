<template>
  <div @click="tabClick" class="tab-bar-item">
    <div v-if="!isActive">
      <slot name="item-icon"></slot>
    </div>
    <div v-else>
      <slot name="item-icon-active"></slot>
    </div>
    <div :style="isActive ? { color: activeColor } : {}">
      <slot name="item-text"></slot>
    </div>
  </div>
</template>

<script>
export default {
  name: "TabBarItem",
  data() {
    return {
      // isActive:true
    };
  },
  props: {
    activeColor: {
      type: String,
      default: "#000",
    },
    path: [String],
  },
  computed: {
    isActive: {
      set() {},
      get() {
        // return this.$route.path.indexOf(this.path) !== -1
        return this.$route.path == this.path;
      },
    },
  },
  methods: {
    tabClick() {
      this.$router.replace(this.path);
      this.isActive = !this.isActive;
    },
  },
};
</script>

<style scoped>
.tab-bar-item {
  flex: 1;
  height: 49px;
  background-color: #fff;
  font-size: 14px;
}

.tab-bar-item img {
  width: 24px;
  height: 24px;
  margin-top: 7px;
  vertical-align: middle;
}
</style>
