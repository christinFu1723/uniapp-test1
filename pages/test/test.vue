<template>
  <view @click="test">测试页面</view>
</template>

<script>
export default {
  data() {
    return {};
  },
  onLoad() {
    const info = getApp().globalData.info;
    console.log(info);
    const res = uni.getStorageSync('test');
    console.log('本地存储数据', res);
  },
  methods: {
    test() {
      let pages = getCurrentPages();
      let index = pages[0].$getAppWebview();
      console.log(index.id);

      uni.$emit('vue-modify', {
        title: 'vue修改nvue'
      });
      uni.switchTab({
        url: '/pages/index/index',
        fail: err => {
          console.log(err);
        }
      });
    }
  }
};
</script>

<style></style>
