<template>
	<view class="content">

		<uni-drawer @change="showContents=!showContents" :width="300" ref="contents" mode="left" :mask-click="true">
			<scroll-view style="height: 100%;" scroll-y="true">
				<view v-for="item in 60" :key="item">可滚动内容 {{ item }}</view>
			</scroll-view>
		</uni-drawer>

	</view>


</template>

<script>
	export default {
		data() {
			return {
				showContents: false,
				url: "https://api.github.com/repos/v012345/notebook/contents"
			}
		},
		components: {

		},
		onLoad() {
			uni.request({
				url: this.url,
			}).then(data => {
				console.log(data)
			})
			// function generateDirectoryTree(url, DirectoryTree, callback) {
			// 	axios.get(url).then((response) => {
			// 		for (const [index, data] of response.data.entries()) {
			// 			let node = {};
			// 			node.id = data.sha;
			// 			node.label = data.name.replace(/\.md/, "");
			// 			node.type = data.type;
			// 			if (data.type == "file") {
			// 				node.download_url = data.download_url;
			// 				DirectoryTree.push(node);
			// 			}
			// 			if (data.type == "dir") {
			// 				node.children = [];
			// 				generateDirectoryTree(data.url, node.children, axios, () => {});
			// 				DirectoryTree.push(node);
			// 			}
			// 			if (index == response.data.length - 1) {
			// 				callback();
			// 			}
			// 		}
			// 	});
			// }
			// new Promise((resolve) => {
			// 	generateDirectoryTree(this.url, this.tree, this.axios, resolve);
			// }).then(() => {
			// 	this.$emit("done");
			// 	this.show = true;
			// });

		},
		onNavigationBarButtonTap() {
			this.showContents ? this.$refs.contents.close() : this.$refs.contents.open();
		},
		methods: {}
	}
</script>

<style lang="scss" scoped>

</style>
