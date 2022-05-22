<template>
	<view class="">
		
	<view class="box">
		发表虫记
	</view>
	<Ucard></Ucard>
	
	</view>
</template>

<script>
	import Ucard from '../index/Ucard.vue'
	export default {
		data() {
			return {
		
			}
		},
		components:{
			Ucard
		}
		}
</script>

<style scoped>
	.box{
		height: 80rpx;
		/* width: 100rpx; */
		background: #1cbbb4;
		margin: 50rpx;
		text-align: center;
		line-height: 80rpx;
		color: white;
		font-weight: bolder;
		border-radius: 15px;
	}
</style>