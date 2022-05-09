<template>
  <div class="wrapper" ref="wrapper">
    <div class="content">
      <slot></slot>
    </div>
  </div>
</template>

<script>
import BScroll from "better-scroll";
import { getHomeGoods } from "@/network/home";

export default {
  name: "Scroll",
  data() {
    return {
      // 用于保存 下面 new Scroll插件的对象
      scroll: null,
    };
  },
  props: {
    // Scroll 中 开启哪种模式 0 1 2 3
    probeType: {
      type: Number,
      default() {
        return 0;
      },
    },
    // Scroll 中 pullUpLoad是否开启
    pullUpLoad: {
      type: Boolean,
      default() {
        return false;
      },
    },
  },
  mounted() {
    // 1.创建scroll对象
    this.scroll = new BScroll(this.$refs.wrapper, {
      click: true, // 是否开启鼠标事件 (作用是:<Scroll></Scroll>组件中的点击事件)
      probeType: this.probeType,
      pullUpLoad: this.pullUpLoad,
    });
    // this.probeType代表: 判断Scroll开启哪种模式 (可由用户传值 :probeType='0/1/2/3') (0和1)代表滚动时不监测 2代表手指还在滚动时的位置 3代表只要还在滚动就监测滚动的位置   减少性能消耗
    if (this.probeType === 2 || this.probeType === 3) {
      // 2.监听滚动的位置
      this.scroll.on("scroll", (position) => {
        this.$emit("scroll", position);
      });
    }
    // this.pullUpLoad代表:判断Scroll是否开启  (可由用户传值 :pullUpLoad='true/false') 以优化性能之用
    if (this.pullUpLoad) {
      // 3.监听scroll滚动到底部
      this.scroll.on("pullingUp", () => {
        // 滑倒底部时发送 pullingUp事件 Home组件进行下一步如何操作(@pullingUp="loadMore")
        this.$emit("pullingUp");
      });
    }
  },
  methods: {
    // 用于 Home组件 backClick 返回顶部事件 x:底部滚动条，y:右边滚动条，time:滚动所需时间 默认值 300ms
    scrollTop(x, y, time = 300) {
      this.scroll && this.scroll.scrollTo(x, y, time);
    },
    // 刷新所监测的Scroll组件
    refresh() {
      this.scroll && this.scroll.refresh();
    },
    // 封装上拉加载时 刷新 (finishPullUp) // 作用是: Home组件可以少写一个scroll scroll为Scroll(本组件) new BScroll 一个对象
    finishPullUp() {
      this.scroll && this.scroll.finishPullUp();
    },
    // 获取当前页面将要deactivated时保存的页面 scroll.y
    getScrollY() {
      return this.scroll ? this.scroll.y : 0;
    },
  },
};
</script>

<style scoped>
</style>
