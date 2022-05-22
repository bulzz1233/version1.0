<template>
	<view>
		<view class="background">

		</view>
		<view class="list" hover-class="active_list">
			<text>重新定位</text>
			<view class="iconfont icon-map icon">
				<text class="text">江门市</text>
			</view>

		</view>
		<view class="list" hover-class="active_list" @click="getphoto()">
			<text>从相册选择</text>
			<text>></text>
		</view>
		<view class="list" hover-class="active_list" @click="gohistory()">
			<text>识别历史</text>
			<text>></text>
		</view>
		<view class="photo_layout">


			<view class="photo" @click="takephoto()">
				<view class="iconfont icon-camera set_camera">

				</view>
			</view>
		</view>
	</view>
</template>

<script>
	import {
		pathToBase64,
		base64ToPath
	} from '../../js_sdk/mmmm-image-tools/index.js'
	export default {
		data() {
			return {
				photo: [],
				url: ''
			}
		},
		methods: {
			getphoto() {
				uni.chooseImage({
					count: 1,
					sizeType: ['original', 'compressed'],
					sourceType: ['album'], //这要注意，camera掉拍照，album是打开手机相册
					success: (res) => {
						pathToBase64(res.tempFilePaths[0])
							.then(base64 => {
								//生成4到8随机数。Math.floor(Math.random()*(max-min+1)+min);	
								let timer = (Math.floor(Math.random() * (7 - 4 + 1) + 4)) * 1000;
								uni.showLoading({
									title: "正在识别",
									mask: true
								});

								setTimeout(() => {
									uni.hideLoading();
									for (let i = 0; i < this.photo.length; i++) {
										if (base64 == this.photo[i]) {
											console.log(true);
											uni.navigateTo({
												url: './history?item=' + i


											})
											break;

										} else if (base64 != this.photo[i] && i == this.photo
											.length - 1) {
											uni.showModal({
												title: '提示',
												content: '识别失败！',
												showCancel: false,
												success: (res) => {
													if (res.confirm) {
														uni.navigateTo({
															url: './history?item=6&base=' +
																encodeURIComponent(
																	JSON
																	.stringify(
																		base64)
																)



														})
													}
												}

											})
											break;
										}

									}

								}, timer)

							})
							.catch(error => {
								console.error(error)
							})

					}
				})
			},
			takephoto() {
				uni.chooseImage({
					count: 1,
					sizeType: ['original', 'compressed'],
					sourceType: ['camera'], //这要注意，camera掉拍照，album是打开手机相册

					success: (res) => {
						pathToBase64(res.tempFilePaths[0])
							.then(base64 => {
								//生成4到8随机数。Math.floor(Math.random()*(max-min+1)+min);	
								let timer = (Math.floor(Math.random() * (7 - 4 + 1) + 4)) * 1000;
								uni.showLoading({
									title: "正在识别",
									mask: true
								});

								setTimeout(() => {
									uni.hideLoading();

									uni.showModal({
										title: '提示',
										content: '识别失败！',
										showCancel: false,
										success: (res) => {
											if (res.confirm) {
												uni.navigateTo({
													url: './history?item=6&base=' +
														encodeURIComponent(JSON
															.stringify(base64))



												})
											}
										}

									})





								}, timer)

							})

					}
				});

			},
			gohistory() {
				uni.navigateTo({
					url: './history?item=5'
				})
			}
		},
		mounted() {
			let url = ["scanning1.jpg", "scanning2.jpg", "scanning3.jpg"]
			for (let i = 0; i < url.length; i++) {
				require("@/static/tookphoto/" + url[i]);
				pathToBase64(require("@/static/tookphoto/" + url[i]))
					.then(base64 => {

						 this.photo.push(base64)


					})
					.catch(error => {
						console.error(error)
					})
			}
			// return this.photo
		}
	}
</script>

<style>
	.background {
		position: absolute;
		height: 100%;
		width: 100%;
		background: aliceblue;
		z-index: -1;
	}

	.list {
		position: relative;
		margin-top: 20rpx;
		margin-bottom: 20rpx;
		padding: 20rpx;
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		align-items: center;
		z-index: 1;
		background: white;
	}

	.icon {
		color: #1cbbb4;
		font-size: 40rpx;
	}

	.text {
		font-size: 30rpx;
	}

	.photo {
		position: relative;
		width: 300rpx;
		height: 300rpx;
		background: #1cbbb4;
		margin: 0;
		display: flex;
		justify-content: center;
		align-items: center;
		border-radius: 50%;
		box-shadow: 0 2px 4px rgba(0, 0, 0, .3), 0 0 6px rgba(0, 0, 0, .3)
	}

	.photo_layout {
		position: relative;
		top: 500rpx;
		display: flex;
		justify-content: center;
		align-items: center;
	}

	.set_camera {
		color: white;
		font-size: 200rpx;
	}

	.active_list {
		background: #d9d9d9;
	}
</style>
