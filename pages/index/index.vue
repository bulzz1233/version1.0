<template>
	<view>
		<view class="swiper">
			<swiper autoplay="true" interval="4000">
				<swiper-item class="content">
					<image class="img" src="../../static/swiper/si.png" mode="heightFix"></image>
				</swiper-item>
				<swiper-item class="content">
					<image class="img" src="../../static/swiper/dao.png" mode="heightFix"></image>
				</swiper-item>
				<swiper-item class="content">
					<image class="img" src="../../static/swiper/cai.png" mode="heightFix"></image>
				</swiper-item>
			</swiper>
		</view>
		<view class="box"></view>

		<view class="extend">
			
			<view class="card" hover-class="card_active" v-for="m in menu" :key="m.id">
				<view class="iconfont icon_style" :class="m.icon"></view>
				<view class="text_style"><text>{{m.text}}</text></view>
			</view>
		</view>

		<view class="box1_style">
			<view class="box1"></view>
		</view>

		<view class="recommend">
			<view class="dataStyle" hover-class="dataStyle_active">
				<view class="recommend_text">
					<text>数据统计</text>
					<view>
						<text>DATA</text>
					</view>
					<view>
						<text>STATISTIC</text>
					</view>

				</view>

				<view class="iconfont icon-data-view setSize">

				</view>
			</view>
			<view class="dataStyle" hover-class="dataStyle_active">
				<view class="recommend_text">
					<text>森防知识</text>
					<view>
						<text>DEFENSE</text>
					</view>
					<view>
						<text>KNOWLEDGE</text>
					</view>

				</view>
				<view class="iconfont icon-explain setSize"></view>
			</view>

		</view>
		
		<view class="title">
			<view class="box3"></view>
			<text class="title_text">虫记圈</text>
		</view>

		<Ucard></Ucard>
		
	</view>


	
</template>

<script>
	import Ucard from './Ucard.vue'
	export default {
		data() {
			return {
				menu: [{
						id: '1',
						icon: 'icon-modular',
						text: '分类查询'
					},
					{
						id: '2',
						icon: 'icon-map',
						text: '勘察轨迹'
					},
					{
						id: '3',
						icon: 'icon-file',
						text: '数据采集'
					},
					{
						id: '4',
						icon: 'icon-complete',
						text: '工作日志'
					},
					{
						id: '5',
						icon: 'icon-image-text',
						text: '新闻资讯'
					},
					{
						id: '6',
						icon: 'icon-user',
						text: '专家鉴定'
					},
					{
						id: '7',
						icon: 'icon-icon-test',
						text: '虫警物联'
					}
				]
			}
		},
		onLoad() {

		},
		methods: {

		},
		components:{
			Ucard
		}
	}
</script>

<style socped>
	.box {
		position: absolute;
		width: 100%;
		height: 680rpx;
		top: -340rpx;
		z-index: -1;
		border-radius: 50%;
		background: #1cbbb4;
	}

	.img {
		height: 100%;
		border-radius: 5px;
	}

	.content {
		display: flex;
		flex-direction: row;
		justify-content: center;
		align-content: center;

	}

	.swiper {
		position: relative;
		margin: 20rpx;


	}

	.card {
		position: relative;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		padding: 10rpx;
		border-radius: 5px;
		margin: 20rpx;
	}

	.icon_style {
		font-size: 80rpx;
		color: #1cbbb4;
	}

	.extend {
		z-index: 2;
		position: relative;
		display: flex;
		flex-direction: row;
		flex-wrap: wrap;
		 justify-content: center; 
		/* align-items: center; */
	}

	.text_style {
		font-size: 15px;
	}

	.box1_style {
		display: flex;
		justify-content: center;
		align-items: center;
		margin: 10rpx;
	}

	.box1 {
		background: #cecece;
		height: 10rpx;
		width: 90%;
		border-radius: 5px;
	}

	.setSize {
		font-size: 110rpx;
		color: white;
	}

	.dataStyle {
		background: #1cbbb4;
		width: 300rpx;
		border-radius: 5px;
		display: flex;
		flex-direction: row;
		justify-content: center;
		align-items: center;
	}

	.recommend {
		display: flex;
		flex-direction: row;
		justify-content: space-around;
		margin-top: 20rpx;
	}
	
.card_active{
	background: #e1e1e1;
}
	.recommend_text {
		color: white;
		margin: 20rpx;
		font-size: 12px;
	}
	.box3{
		width: 10rpx;
		height: 60rpx;
		background: #cecece;
	}
	.title{
		display: flex;
		flex-direction: row;
		font-size: 17px;
		font-weight: bolder;
		margin: 30rpx;
		
	}
	.title_text{
		margin-left: 15rpx;
		
	}
	.dataStyle_active{
		background: #16948e;
	}

</style>
