<template>
	<view class="card_layout">
		<view v-show="!show" class="background">
			暂无识别
		</view>
		<view v-show="show" class="btn_layout">
			<view class="inter">
				<view @click="clear()" class="btn">
					清空历史
				</view>
			</view>
		</view>
		<view v-show="show" class="card" v-for="(li,index) in list" :key="index">
			<view class="top">
				<text v-show="li.showtitle" class="top_text">识别成功</text>
				<text v-show="!li.showtitle" class="top_text">识别失败</text>
				<text class="time">上传时间{{li.time}}</text>
			</view>
			<view class="pic">
				<image :src="li.pic"></image>
			</view>
			<view class="bottom">
				<view class="text_layout"><text>害虫类别</text><text class="bottom_text">{{li.type}}</text></view>
				<view class="text_layout"><text>数量统计</text><text class="bottom_text"></text>{{li.count}}</view>
				<view class="text_layout"><text>为害农作物</text><text class="bottom_text"></text>{{li.likes}}</view>
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
				list: [],
				listdata: [{

						pic: "/static/tookphoto/done1.jpg",
						type: '害虫',
						count: '3',
						likes: '小麦',
						showtitle: true
					},
					{

						pic: "/static/tookphoto/done2.jpg",
						type: '害虫',
						count: '2',
						likes: '水稻',
						showtitle: true
					},
					{

						pic: "/static/tookphoto/done3.jpg",
						type: '害虫',
						count: '4',
						likes: '玉米',
						showtitle: true
					}


				],
				timer: '',
				show: false

			}
		},
		onLoad(option) {
			const item = option.item
			// console.log(item)
			//获取当时时间
			let date = new Date();
			let year = date.getFullYear();
			let month = date.getMonth() + 1;
			let day = date.getDate();
			let hour = date.getHours() < 10 ? "0" + date.getHours() : date.getHours();
			let minute = date.getMinutes() < 10 ? "0" + date.getMinutes() : date.getMinutes();
			month >= 1 && month <= 9 ? (month = "0" + month) : "";
			day >= 0 && day <= 9 ? (day = "0" + day) : "";
			let timer = year + '-' + month + '-' + day + ' ' + hour + ':' + minute;
			this.timer = timer
			if (item == 5) {
				uni.getStorage({
					key: 'list_data',
					success: res => {
						// console.log(res.data)
						this.show = true
						this.list = res.data
					},
					fail() {
						console.log(99)
					}

				})

			} else if (item == 6) {
				if (option.base != null) {
					this.show = true
					const p = JSON.parse(decodeURIComponent(option.base));
					base64ToPath(p).then(path => {
						// console.log(path)

						uni.getStorage({
							key: 'list_data',
							success: res => {
								this.show = true
								this.list = res.data
								let obj1 = this.listdata[0]

								obj1['pic'] = path;
								obj1['type'] = '无法识别';
								obj1['count'] = '无法识别';
								obj1['likes'] = '无法识别';
								obj1['time'] = timer;
								obj1['showtitle'] = false;
								this.list.push(obj1)
								// console.log('2'+this.list)
								uni.setStorage({
									key: 'list_data',
									data: this.list
								})

							},
							fail: res => {
								this.show = true
								let obj2 = this.listdata[0]

								obj2['pic'] = path;
								obj2['type'] = '无法识别';
								obj2['count'] = '无法识别';
								obj2['likes'] = '无法识别';
								obj2['time'] = timer;
								obj2['showtitle'] = false;
								this.list.push(obj2)
								
								uni.setStorage({
									key: 'list_data',
									data: this.list
								})
							}

						})


					}).catch(error => {
						console.log(error)
					})
				}
			} else {
				let obj = this.listdata[option.item]
				let time1 = "time"
				obj[time1] = timer
				uni.getStorage({
					key: 'list_data',
					success: res => {
						this.show = true
						this.list = res.data
						this.list.push(obj)

						uni.setStorage({
							key: 'list_data',
							data: this.list

						})
					},
					fail: res => {
						this.show = true
						this.list.push(obj)

						uni.setStorage({
							key: 'list_data',
							data: this.list

						})

					}

				})


			}

		},
		methods: {
			clear() {
				uni.showModal({
					title: '提示',
					content: '确认要清除历史信息吗？',
					success: (res) => {
						if (res.confirm) {
							uni.removeStorage({
								key: 'list_data',
								success: (res) => {
									this.list = []
									this.show = false
								}
							});
						}
					}

				})
			}
		}

	}
</script>

<style scoped>
	.pic {

		width: 90%;
		overflow: hidden;

	}

	.background {

		position: fixed;
		width: 100%;
		height: 100%;
		background: aliceblue;
		color: #444546;
		display: flex;
		justify-content: center;
		align-items: center;
	}

	.card {
		position: relative;
		margin-top: 20rpx;
		/* width: 100%; */
		border: 1rpx solid #e4e7eb;
		display: flex;
		flex-direction: column;
		/* justify-content: center; */
		align-items: center;
		border-radius: 5px;
		padding: 20rpx;
	}

	.card_layout {
		position: relative;

	}

	.top {
		position: relative;
		width: 90%;
		margin: 15rpx;
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		/* align-items: space-between; */
	}

	.top_text {

		letter-spacing: 15rpx;
		font-weight: bolder;
	}

	.time {
		font-size: 25rpx;
		font-weight: bolder;
		display: flex;
		justify-content: center;
		align-items: center;
	}

	.bottom {
		width: 90%;
		display: flex;
		flex-direction: column;
		margin-top: 10rpx;
		margin-bottom: 10rpx;
		/* justify-content: saf */
	}

	.text_layout {
		width: 50%;
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		margin-top: 10rpx;
		font-size: 25rpx;
		color: #444546;
		font-weight: bolder;
	}

	.bottom_text {
		margin-left: 80rpx;
	}

	.btn_layout {
		position: relative;
		width: 90%;

		margin-top: 30rpx;
	}

	.inter {
		display: flex;
		justify-content: end;
		width: 100%;
	}

	.btn {
		display: flex;
		justify-content: center;
		align-items: center;
		background: #1cbbb4;
		width: 130rpx;
		height: 55rpx;
		border-radius: 10px;
		font-size: 20rpx;
		color: white;
		box-shadow: 0 2px 4px rgba(0, 0, 0, .2), 0 0 6px rgba(0, 0, 0, .2)
	}
</style>
