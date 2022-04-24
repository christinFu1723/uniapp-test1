<template>
  <view style="width: 372.5rpx;">
    <image :src="item.cover" mode="widthFix" lazy-load></image>
    <view class="font-md">{{ item.title }}</view>
    <text class="font d-block text-light-muted ">{{ item.desc }}</text>
    <view class="d-flex my-1">
      <price>
        <view slot="price">{{ item.price1 }}</view>
      </price>
      <view class="font-sm text-light-muted line-through ml-1 a-self-end line-h">
        $ {{ item.price2 }}
      </view>
    </view>
  </view>
</template>

<script>
  import price from '@/components/common/price.vue';
export default {
  components:{ price},
  props: {
    item: {
      type: Object,
      default: () => {}
    }
  }
};
</script>

<style></style>
