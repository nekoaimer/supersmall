<template>
  <div>
    <Swiper>
      <SwiperItem v-for="item in banners.list">
        <a :href="item.link"
          ><img :src="item.image" alt="" @load="swiperImageLoad"
        /></a>
      </SwiperItem>
    </Swiper>
  </div>
</template>

<script>
import { Swiper, SwiperItem } from "@/components/common/swiper";
// import {getHomeMultidata} from 'network/home'

export default {
  name: "HomeSwiper",
  data() {
    return {
      isLoad: false,
    };
  },
  props: {
    banners: {
      type: Object,
      default() {
        return {};
      },
    },
    recommends: {
      type: Object,
      default() {
        return {};
      },
    },
  },
  methods: {
    swiperImageLoad() {
      if (!this.load) {
        this.$emit("swiperImageLoad");
        this.load = true;
      }
    },
  },
  // data() {
  //   return {
  //     banners: [],
  //     recommends: [],
  //     animDuration:500
  //   }
  // },
  components: {
    Swiper,
    SwiperItem,
  },
  // created() {
  //   getHomeMultidata().then(res => {
  //     // console.log(res, 'res')
  //     this.banners = res.data.banner
  //     this.recommends = res.data.recommend
  //   }).catch(err => {
  //     // console.log(err, 'err')
  //   })
  // }
};
</script>

<style scoped>
</style>
