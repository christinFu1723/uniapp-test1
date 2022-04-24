<template>
  <view class="row j-center m-2">
    <block v-for="(item,index) in icons" :key="index">
      <view class="span-4 d-flex flex-column j-center a-center py-1">
        <image :src="item.src" style="width: 60rpx;height: 60rpx;" ></image>
        <text class="font-sm">新品发布</text>
      </view>
    </block>
  </view>
</template>

<script>

export default {
  props:{
    icons:{
      type:Array,
      default:()=>[]
    }
  },
  data() {
    return {
     
    };
  },
  onLoad() {},
  methods: {}
};
</script>

<style></style>
