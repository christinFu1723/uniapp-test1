<template>
  <view >
    <swiper :indicator-dots="true" :autoplay="true" :interval="3000" :duration="1000">
      <swiper-item v-for="(item, index) in swipers" :key="index" @tap="handleTap(item)">
        <image :src="item.src" :lazy-load="true" style="height: 350rpx;" mode="widthFix"></image>
      </swiper-item>
    </swiper>
  </view>
</template>

<script>
export default {
  props:{
    swipers:{
      type:Array,
      default:()=>[]
    }
    
  },
  data() {
    return {

    };
  },
  onLoad() {},
  methods: {
    handleTap(item){}
  }
};
</script>

<style></style>
