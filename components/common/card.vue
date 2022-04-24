<template>
  <view class="card">
    <view class=" p-1 border-bottom">
      <slot name="title">
        <view v-if="headTitle" class="font-md font-weight ">{{ headTitle }}</view>
      </slot>
    </view>
    <view>
      <image v-if="bodyCover" :src="bodyCover" mode="widthFix" />
      <slot name="body"></slot>
    </view>
  </view>
</template>

<script>
export default {
  props: {
    headTitle: {
      type: String,
      default: ''
    },
    bodyCover: {
      type: String,
      default: ''
    }
  }
};
</script>

<style></style>
