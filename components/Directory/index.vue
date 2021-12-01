<template>
	<view class="container">
		<view class="background" @touchmove.stop.prevent="">
		</view>
		<view class="main" scroll-y='true'>
			<view v-for="i in 100" :key="i">
				{{i}}
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title: 'Hello'
			}
		},
		onLoad() {

		},
		methods: {

		}
	}
</script>

<style lang="scss" scoped>
	$main-width: 88vw;

	.container {
		box-sizing: border-box;
		height: 100vh;
		width: 100vw;


		position: fixed;
		top: 0;
		left: 0;

		overflow-x: hidden;

		.background {
			height: 100vh;
			width: 100vw;
			background-color: rgba($color: #000000, $alpha: .5);
		}

		.main {
			position: fixed;
			top: 0;
			left: 0;
			
			width: $main-width;
			height: 100vh;
			background-color: green;
			overflow-y: scroll;
		}


	}
</style>
