<template>
	<view class="">
		<button @click="open">打开弹窗</button>
		<uni-popup ref="popup" type="dialog">
			<uni-popup-dialog title="例如:v012345/notebook" mode="input" message="成功消息" :duration="2000"
				:before-close="true" @close="close" @confirm="confirm" placeholder="用户名/仓库名"></uni-popup-dialog>
		</uni-popup>
		<uni-card>
			<text>这是一个基础卡片示例，内容较少，此示例展示了一个没有任何属性不带阴影的卡片。</text>
		</uni-card>
		<uni-card title="基础卡片" extra="额外信息">
			<text>这是一个基础卡片示例，此示例展示了一个标题加标题额外信息的标准卡片。</text>
		</uni-card>
		<uni-card title="基础卡片" sub-title="副标题" extra="额外信息" thumbnail="https://avatars.githubusercontent.com/v012345">
			<text>这是一个带头像和双标题的基础卡片，此示例展示了一个完整的卡片。</text>
		</uni-card>
		<uni-card title="基础卡片" sub-title="副标题" extra="额外信息"
			thumbnail="https://vkceyugu.cdn.bspapp.com/VKCEYUGU-dc-site/460d46d0-4fcc-11eb-8ff1-d5dcf8779628.png">
			<text>这是一个带头像和双标题的基础卡片，此示例展示了一个完整的卡片。</text>
		</uni-card>
		<uni-card sub-title="副标题" extra="额外信息" thumbnail="https://avatars.githubusercontent.com/v012345"
			cover="https://raw.githubusercontent.com/v012345/notebook/master/assets/cover.png">
			<!-- <image slot='cover' style="width: 100%;" :src="cover"></image> -->
			<text>这是一个带封面和操作栏的卡片示例，此示例展示了封面插槽和操作栏插槽的用法。</text>
		</uni-card>
		<uni-card cover="https://vkceyugu.cdn.bspapp.com/VKCEYUGU-dc-site/460d46d0-4fcc-11eb-8ff1-d5dcf8779628.png">
			<!-- <image slot='cover' style="width: 100%;" :src="cover"></image> -->
			<text>这是一个带封面和操作栏的卡片示例，此示例展示了封面插槽和操作栏插槽的用法。</text>
			<view slot="actions" class="card-actions">
				<view class="card-actions-item" @click="actionsClick('分享')">
					<uni-icons type="pengyouquan" size="18" color="#999"></uni-icons>
					<text class="card-actions-item-text">分享</text>
				</view>
				<view class="card-actions-item" @click="actionsClick('点赞')">
					<uni-icons type="heart" size="18" color="#999"></uni-icons>
					<text class="card-actions-item-text">点赞</text>
				</view>
				<view class="card-actions-item" @click="actionsClick('评论')">
					<uni-icons type="chatbubble" size="18" color="#999"></uni-icons>
					<text class="card-actions-item-text">评论</text>
				</view>
			</view>
		</uni-card>
	</view>
</template>

<script>
	export default {
		methods: {
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
				// 输入框的值
				console.log(value)
				// TODO 做一些其他的事情，手动执行 close 才会关闭对话框
				// ...
				this.$refs.popup.close()
			}
		}
	}
</script>

<style>
</style>
