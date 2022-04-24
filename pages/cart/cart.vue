<template>
	<view>
		33223
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
    onLoad(){
       console.log('加载购物车');
        uni.$emit('vue-test', { title: 'vue事件传值' });
    },
		methods: {
			
		}
	}
</script>

<style>

</style>
