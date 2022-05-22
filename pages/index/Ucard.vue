<template>
	<view class="card_layout">
		<view class="card" v-for="p in user_data" :key="p.id">
			<view class="user">
				<view class="user-inter">
				<view class="layout">


					<view class="face1">

					</view>
					<view class="user_layout">
						<view class="username"> {{p.username}}</view>
						<view class="posttime">
							{{p.posttime}}
						</view>
					</view>

				</view>
				
				<view class="iconfont icon-elipsis setSize">
				</view>
				</view>
			</view>

			<view class="content1">
				<view class="content">
				{{p.content}}
				</view>
			</view>
			<view class="pic">
				<image style="position: relative;" :src="p.pic" mode="widthFix"></image>
			</view>
			<view class="menu1">
				<view class="iconfont icon-navigation text">

				</view>
				<view class="iconfont icon-comment text">
					<text class="text_style1">{{p.comment}}</text>
				</view>
				<view class="iconfont icon-fabulous text" :class="btn?'active':''" @click="active">
					<text class="text_style1">{{p.likes}}</text>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		name: 'Ucard',
		data() {
			return {
				btn: false,
				user_data: [{
						id: "1",
						username: "小明",
						posttime: "2022-5-19 19:00",
						content: "这是什么虫",
						pic: "../../static/ucard/1.png",
						comment: 11,
						likes: 20
					},
					{
						id: "2",
						username: "小红",
						posttime: "2022-5-18 14:30",
						content: "这个虫子好丑",
						pic: "../../static/ucard/2.png",
						comment: 41,
						likes: 60
					},
					{
						id: "3",
						username: "小黄",
						posttime: "2022-5-17 15:00",
						content: "怎样可以防治害虫呢",
						pic: "../../static/ucard/1.png",
						comment: 5,
						likes: 4
					}
				]
			}
		},
		methods: {
			active() {
				this.btn = !this.btn
			}
		},
	}
</script>

<style scoped>
	.card_layout {
		position: relative;
		width: 100%;


	}


	.user {
		position: relative;
		width: 85%;
	}

	.layout {
		display: flex;
		flex-direction: row;
		justify-content: space-between;
	}

	.user_layout {

		display: flex;
		flex-direction: column;
		margin-left: 30rpx;
		position: relative;
	}

	.face1 {
		width: 100rpx;
		height: 100rpx;
		background: #ccc;
		border-radius: 50%;
	}

	.content1 {
		position: relative;
		width: 85%;
		margin: 20rpx;


	}

	.username {

		font-weight: bolder;
		font-size: 35rpx;
	}

	.posttime {
		color: #ccc;
		font-size: 30rpx;
	}

	.pic {
		position: relative;
		height: 500rpx;
		overflow: hidden;
		display: flex;
		margin: 30rpx;

	}

	.setSize {
		font-size: 70rpx;
		color: #ccc;
		margin-left: 100rpx;
	}

	.menu1 {
		display: flex;
		flex-direction: row;
		justify-content: space-around;
		width: 100%;
		margin-bottom: 50rpx;


	}

	.text {
		font-size: 50rpx;
		color: #6a6a6a;
	}

	.text_style1 {
		font-size: 20rpx;
		margin-left: 10rpx;
	}

	.active {
		color: #1cbbb4;
	}

	.card {
		display: flex;
		flex-direction: column;

		align-items: center;
	}
	.user-inter{
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		width: 100%;
	}
	.content{
		display: flex;
		justify-content: start;
		width: 100%;
	}
</style>
