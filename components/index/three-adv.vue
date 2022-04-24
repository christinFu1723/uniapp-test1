<template>
  <view class="d-flex">
    <image :src="data.left.src" lazy-load class="leftCtn"></image>
    <view class="d-flex flex-column">
      <image :src="data.rightTop.src" lazy-load class="rightTopCtn"></image>
      <image :src="data.rightBtm.src" lazy-load class="rightBtmCtn"></image>
    </view>
  </view>
</template>

<script>
export default {
  props: {
    data: {
      type: Object,
      default: () => {}
    }
  }
};
</script>

<style lang="scss" scoped>
.leftCtn {
  width: 373rpx;
  height: 530rpx;
  border-right: 2rpx solid #f5f5f5;
}
.rightTopCtn {
  width: 375rpx;
  height: 264rpx;
  border-bottom: 2rpx solid #f5f5f5;
}
.rightBtmCtn {
  width: 375rpx;
  height: 264rpx;
}
</style>
