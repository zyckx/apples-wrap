<template>
	<Layout mode='zoom' show="show">
		<view class="content">
			<image class="logo" src="/static/logo.png"></image>
			<view class="text-area">
				<u-alert :title="title" type="primary"></u-alert>
			</view>
			<view class="identify-box">
				<view class="take-photo" @click="takePhoto">
				</view>
				<view class="upload-image" @click="chooseImage">
				</view>
			</view>
		</view>
	</Layout>
</template>

<script setup>
	import {
		ref
	} from "vue";
	import Layout from '../../components/Layout/Layout.vue'
	const title = ref('欢迎使用苹果套袋识别系统')

	const takePhoto = () => {
		uni.chooseImage({
			count: 1, //选择一张
			sizeType: ['original', 'compressed'], //可以指定是原图还是压缩图，默认二者都有
			sourceType: ['camera'], //从相册选择
			success: function(res) {
				console.log(JSON.stringify(res.tempFilePaths));
			}
		});
	}
	const chooseImage = () => {
		console.log("choose image")
		uni.chooseImage({
			count: 1, //选择一张
			sizeType: ['original', 'compressed'], //可以指定是原图还是压缩图，默认二者都有
			sourceType: ['album'], //从相册选择
			success: function(res) {
				console.log(JSON.stringify(res.tempFilePaths));
			}
		});
	}
	const uploadImage = () => {
		console.log("upload image")
	}
	const identify = () => {
		console.log("identify.......")
	}
</script>

<style lang="scss">
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;

		.logo {
			height: 200rpx;
			width: 200rpx;
			margin-top: 200rpx;
			margin-left: auto;
			margin-right: auto;
			margin-bottom: 50rpx;
		}

		.text-area {
			display: flex;
			justify-content: space-between;
			flex-direction: column;

			.title {
				font-size: 36rpx;
				color: #8f8f94;
			}
		}

		.identify-box {
			width: 100%;
			margin-top: 120upx;
			min-height: 400upx;
			display: flex;
			justify-content: space-around;
			// align-items: center;

			.take-photo,
			.upload-image {
				width: 200upx;
				height: 200upx;
				background-color: #8f8f94;
			}

			.take-photo {
				background: url("../../static/images/拍照.png")no-repeat;
				background-size: cover;
				background-position: 0 0;
			}

			.upload-image {
				background: url("../../static/images/上传.png")no-repeat;
				background-size: cover;
				background-position: 0 0;
			}
		}
	}
</style>