<template>
	<view class="content">
		
		<image class="logo" src="/static/logo.png"></image>
		<view class="text-area">
			<text class="title">{{title}}</text>
		</view>
		<navigator url="../profile/index">
			<button type="default">123123123</button>
		</navigator>
		<image class="logo" src="/static/logo.png"></image>
		<view class="text-area">
			<text class="title">{{title}}</text>
		</view>
		<navigator url="../profile/index">
			<button type="default">123123123</button>
		</navigator>
		<image class="logo" src="/static/logo.png"></image>
		<view class="text-area">
			<text class="title">{{title}}</text>
		</view>
		<navigator url="../profile/index">
			<button type="default">123123123</button>
		</navigator>
		<image class="logo" src="/static/logo.png"></image>
		<view class="text-area">
			<text class="title">{{title}}</text>
		</view>
		<navigator url="../profile/index">
			<button type="default">123123123</button>
		</navigator>
		<Directory></Directory>
	</view>


</template>

<script>
	import Directory from "@/components/Directory/index.vue";
	export default {
		data() {
			return {
				title: 'Hello'
			}
		},
		components: {
			Directory,
		},
		onLoad() {

		},
		methods: {

		}
	}
</script>

<style lang="scss" scoped>

</style>
