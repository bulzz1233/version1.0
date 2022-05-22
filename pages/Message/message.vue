<template>
	<view>


		<view class="background">

		</view>
		<view class="list" v-for="m in message" :key="m.id">

			<view class="content">
				<view class="face" :class="m.class">

				</view>
				<view class="user">
				<view class="username">
					{{m.username}}
				</view>
				<view class="text">
					{{m.content}}
				</view>
				</view>
			</view>
			<view class="time">
				<text>{{m.time}}</text>
			</view>
		</view>

	</view>
</template>

<script>
	export default {

		data() {
			return {
				message:[
					{id:'1',username:'系统通知',content:'本社区一周年庆...',time:'20：03',class:'yellow'},
					{id:'2',username:'小红',content:'你好',time:'5月18日',class:'red'},
					{id:'3',username:'小绿',content:'这是什么东西',time:'5月17日',class:'green'},
					{id:'4',username:'小紫',content:'哈哈哈',time:'5月16日',class:'purple'},
					{id:'5',username:'小陈',content:'嗯嗯',time:'5月16日',class:'orange'}
				]
			}
		}
	}
</script>

<style>
	.yellow{
		background: #ffff7f;
	}
	.green{
		background: #aaff7f;
	}
	.red{
		background: #ff557f;
	}
	.purple{
		background: #ff55ff;
	}
	.orange{
		background: #ffaa00;
	}
	.background {
		position: absolute;
		height: 100%;
		width: 100%;
		background: aliceblue;
		z-index: -1;
	}

	.list {
		background: white;
		padding: 10rpx;
		display: flex;
		justify-content: space-between;
		margin-top: 20rpx;
		margin-bottom: 20rpx;
	}
	.face {
		width: 100rpx;
		height: 100rpx;
		
		border-radius: 50%;
	}
	.time{
		display: flex;
		justify-content: center;
		align-items: center;
		font-size: 25rpx;
		color: #ccc;
	}
	.content{
		display: flex;
		flex-direction: row;
	}
	.user{
		display: flex;
		flex-direction: column;
		margin-left: 30rpx;
		justify-content: center;
		
	}
	.username{
		font-size: 30rpx;
		font-weight: bolder;
	}
	.text{
		font-size:25rpx;
		margin: 5rpx;
		color: #ccc;
	}
</style>
