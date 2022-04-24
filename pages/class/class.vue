<template>
  <view>11111{{ title }}</view>
</template>

<script>
export default {
  data() {
    return {
      title: ''
    };
  },
  onLoad() {
    console.log('加载');
    uni.$on('nvue', data => {
      console.log('触发！！！');
      this.title = data.title;
    });

    uni.$on('vue-test', data => {
      console.log('触发2222！！！');
      this.title = data.title;
    });
  },
  onUnload() {
    uni.$off('vue-test');
    uni.$off('nvue');
  },

  methods: {}
};
</script>

<style></style>
