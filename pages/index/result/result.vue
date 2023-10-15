<template>
	<view class="result">
		<div class="img-box">
			<image :src="result.save_path" mode="widthFix" style="width: 100vw;"></image>
		</div>
		<div class="result-box">
			<u-button type="success">识别结果</u-button>
			<div class="text"
				style="margin: 20upx; color: red;display: flex;justify-content: center;align-items: center;">
				{{result.result}}
			</div>
			<u-button type="warning">苹果个数</u-button>
			<div class="text"
				style="margin: 20upx; color: red;display: flex;justify-content: center;align-items: center;">
				{{result.count}}
			</div>
			<u-button type="primary" @click="goback">返回</u-button>
		</div>

	</view>
</template>

<script setup>
	import {
		onShow
	} from "@dcloudio/uni-app"
	import {
		ref
	} from "vue";
	onShow(() => {})
	const result = ref({})
	onShow(() => {
		result.value = uni.getStorageSync("resultlIst")
	})
	const goback = () => {
		uni.navigateBack()
	}
</script>

<style lang="scss">
	.result {
		width: 100%;
		height: 100%;
		display: flex;
		// justify-content: center;
		// align-items: center;
		flex-direction: column;

		.img-box {
			width: 200upx;
		}
	}
</style>