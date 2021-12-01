<template>
	<view class="content">

		<uni-card title="Title Text" thumbnail="" extra="Extra Information" note="Tips">
			The body of the content, you can customize the content and style
		</uni-card> <!-- <Directory></Directory> -->
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
