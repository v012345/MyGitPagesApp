<template>
	<view class="">
		<!-- <button @click="open">打开弹窗</button> -->
		<uni-popup ref="popup" type="dialog">
			<uni-popup-dialog title="例如:v012345/notebook" mode="input" message="成功消息" :duration="2000"
				:before-close="true" @close="close" @confirm="confirm" placeholder="用户名/仓库名"></uni-popup-dialog>
		</uni-popup>

		<view class="book-shelf">
			<view class="booknote" v-for="i in 9" :key="i">
				<uni-card title="notebook" :isFull="true" sub-title="v012345"
					thumbnail="https://avatars.githubusercontent.com/v012345">
					<image class="cover"
						src="https://raw.githubusercontent.com/v012345/notebook/master/assets/cover.png" mode="widthFix"
						@error="imageError"></image>
					<view slot="actions" class="card-actions">
						<view class="card-actions-item" @click="actionsClick('点赞')">
							<uni-icons type="star" size="18" color="#999"></uni-icons>
							<text class="card-actions-item-text">收藏</text>
						</view>
						<view class="card-actions-item" @click="actionsClick('评论')">
							<uni-icons type="trash" size="18" color="#999"></uni-icons>
							<text class="card-actions-item-text">删除</text>
						</view>
					</view>
				</uni-card>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {

			}
		},
		onNavigationBarButtonTap() {
			// console.log(e)
			this.$refs.popup.open()
		},
		onLoad() {
			try {
				const value = uni.getStorageSync('notebooks');
				console.log(value);
				if (value) {
					console.log(value);
				}
			} catch (e) {
				console.log(e);
				// error
			}
			uni.startPullDownRefresh();

			// uni.request({
			// 		url: 'https://www.example.com/request'
			// 	})
			// 	.then(data => {
			// 		// data为一个数组
			// 		// 数组第一项为错误信息 即为 fail 回调
			// 		// 第二项为返回数据
			// 		var [err, res] = data;
			// 		console.log(res.data);
			// 	})
		},
		onPullDownRefresh() {
			console.log('refresh');
			setTimeout(function() {
				uni.stopPullDownRefresh();
			}, 1000);
		},
		methods: {
			imageError: function(e) {
				console.error('image发生error事件，携带值为' + e.detail.errMsg)
			},
			actionsClick() {},
			open() {
				this.$refs.popup.open()
			},
			/**
			 * 点击取消按钮触发
			 * @param {Object} done
			 */
			close() {
				// TODO 做一些其他的事情，before-close 为true的情况下，手动执行 close 才会关闭对话框
				// ...
				this.$refs.popup.close()
			},
			/**
			 * 点击确认按钮触发
			 * @param {Object} done
			 * @param {Object} value
			 */
			confirm(value) {
				let result = value.match(/^(?:(?:http(?:s)?:\/\/)?github.com\/)?([\w-]+)\/([\w-]+)$/mi)
				if (!result) {
					uni.showToast({
						title: '不合法地址',
						duration: 1500,
						icon: "error"
					});
					return
				}
				uni.request({
						url: `https://api.github.com/users/${result[1]}`,
						header: {
							'Accept': 'application/vnd.github.v3+json' //自定义请求头信息
						}
					})
					.then(data => {
						// data为一个数组
						// 数组第一项为错误信息 即为 fail 回调
						// 第二项为返回数据
						var [err, res] = data;
						console.log(res.data);
					})
				console.log(result[1])
				console.log(result[2])
				this.$refs.popup.close()
			}
		}
	}
</script>

<style lang="scss" scoped>
	.book-shelf {
		display: flex;
		flex-wrap: wrap;

		.booknote {
			box-sizing: border-box;
			width: 50%;
			padding: 0.5rem;

			.cover {
				width: 100%;
			}

			.card-actions {
				display: flex;
				flex-direction: row;
				justify-content: space-around;
				align-items: center;
				height: 45px;
				border-top: 1px #eee solid;

				.card-actions-item {
					display: flex;
					flex-direction: row;
					align-items: center;

					.card-actions-item-text {
						font-size: 12px;
						color: #666;
						margin-left: 5px;
					}
				}
			}
		}
	}
</style>
