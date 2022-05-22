<template>
	<view>
		<view class="box"></view>
		<view class="background">
		
		</view>
		<view class="user">
			<view class="face">
				<image src="../../static/user/0.png" class="img"></image>
			</view>
			<view class="username">
				youke 165345637484
			</view>
			<view class="id">
				ID:14945
			</view>
		</view>
		<view class="list" hover-class="active_list" v-for="l in list " :key="l.id">
			<view class="iconfont  setfont" :class="l.class">
			<text class="text">{{l.title}}</text>	
			</view>
			<text>></text>

		
		</view>
	</view>
</template>

<script>
	
	export default {
		data() {
			return {
		list:[
			{id:'1',class:'icon-edit',title:'我的虫记'},
			{id:'2',class:'icon-layers',title:'当前积分'},
			{id:'3',class:'icon-mobile-phone',title:'绑定手机'},
			{id:'4',class:'icon-email',title:'绑定邮箱'},
			{id:'5',class:'icon-lock',title:'修改密码'},
			{id:'6',class:'icon-prompt',title:'关于我们'},
			{id:'7',class:'icon-manage-order',title:'意见反馈'},
			]
			}
		},

		}
</script>
<style scoped>
	.background {
		position: absolute;
		height: 100%;
		width: 100%;
		background: aliceblue;
		z-index: -2;
	}
	
	.list {
		position: relative;
		
		margin-bottom: 20rpx;
		padding: 20rpx;
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		align-items: center;
		z-index: 1;
		background: white;
	}
	.setfont{
		color: #1cbbb4;
		font-size: 45rpx;
	}
	.text{
		margin-left: 30rpx;
		font-size: 30rpx;
		color: black;
	}
	.active_list{
		background: #d9d9d9;
	}
	.box {
		position: absolute;
		width: 100%;
		height: 750rpx;
		top: -400rpx;
		z-index: -1;
		border-radius: 50%;
		background: #1cbbb4;
	}
	.face {
		position: relative;
		width: 200rpx;
		height: 200rpx;
		background: #d9d9d9;
		border-radius: 50%;
		margin: 10rpx;
		overflow: hidden;
	}
	.user{
		height: 350rpx;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		margin: 10rpx;
		margin-bottom: 100rpx;
	}
	.username{
		color: white;
	}
	.id{
		color: white;
	}
	.img{
		position: absolute;
		width: 100%;
		height: 100%;
	}
</style>