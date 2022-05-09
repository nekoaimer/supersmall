<template>
  <div class="goods-item" @click="itemClick" >
    <div>
      <img :src="goodsItem.show.img" alt="" @load="imageLoad">
      <div class="goods-info">
        <p>{{ goodsItem.title }}</p>
        <span class="price">{{ goodsItem.price }}</span>
        <span class="collect">{{ goodsItem.cfav }}</span>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  name: "GoodsListItem",
  data() {
    return {}
  },
  props: {
    goodsItem: {
      type: Object,
      default() {
        return {}
      }
    }
  },
  methods: {
    imageLoad() {
      this.$bus.$emit('itemImageLoad')
    },
    itemClick(){
     // this.$router.replace('/detail')
      this.$router.push({
        path:'/detail',
        query:{iid:this.goodsItem.iid}
      })
    }
  }
}
</script>

<style scoped>
.goods-item {
  /*display: flex;*/
  /*margin: 0px 1px;*/
  width: 48%;
  cursor: pointer;
}

.goods-item img {
  display: inline-block;
  width: 100%;
  height: 100%;
  border-radius: 5px;
}

.goods-info {
  margin: 5px 0;
  text-align: center;
}

.goods-info p {
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;
  width: 100%;
  font-size: 14px;
  margin-bottom: 5px;
}

.goods-info .price {
  /*display: inline-block;*/
  margin: 0 6px 0 -20px;
  font-size: 14px;
  color: var(--color-high-text);
}

.goods-info .collect {
  position: relative;
  left: 15px;
  font-size: 14px;
}

.goods-info .collect::before {
  content: '';
  position: absolute;
  left: -16px;
  top: -1px;
  width: 14px;
  height: 14px;
  background: url("~assets/img/common/collect.svg") 0 0/14px 14px;
}
</style>
