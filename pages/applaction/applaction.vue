<template>
	<Layout mode='zoom' show="show">
		<view class="application">
			<div class="search">
				<u-search placeholder="日照香炉生紫烟" v-model="keyword" @search="searchSubmit"></u-search>
			</div>
			<div class="img">
				<image src="https://www.facaishur.com/uploads/allimg/210112/25-2101121S913962.jpg" mode="widthFix"
					style="width: 100vw;">
				</image>
			</div>
			<div class="article-list">
				<u-collapse>
					<u-collapse-item v-for="item in articleList" :key="item.id" :title="item.title" name="Docs guide">
						<view style="text-indent: 2em;" class="u-collapse-content">{{item.description}}</view>
					</u-collapse-item>
				</u-collapse>
			</div>
		</view>
	</Layout>
</template>

<script setup>
	import Layout from '../../components/Layout/Layout.vue'
	import BackTop from '../../components/BackTop/BackTop.vue'

	import {
		onLoad,
		onPageScroll
	} from '@dcloudio/uni-app'
	onLoad(() => {})
	onPageScroll(() => {})
	import {
		reactive,
		ref
	} from "vue";

	const keyword = ref(null)
	const show = ref(true)
	const scrollTopStyle = reactive({
		iconStyle: {
			fontSize: '32rpx',
			color: '#2979ff'
		}
	})
	const searchSubmit = (e) => {
		console.log(e)
	}
	const appleBenefits = {
		"促进着色": "",
		"减少农药": "",
		"预防害虫": "",
		"养殖方法": ""
	};


	const articleList = ref([{
		id: 1,
		title: "促进着色",
		description: "苹果套袋的作用，可以使用外灰内黑或者内袋红色的双层袋子，使苹果的果面为鲜红色，提高全红苹果的比例，并且经过套袋的苹果不容易皱皮和失去水分，可以较长的保存果实的新鲜度。"
	}, {
		id: 2,
		title: "减少农药",
		description: "苹果套袋有减少农药残留的作用，养殖苹果时，需要使用质量较为优良的单层袋，防止农药接触到苹果，减少农药的残留，在给苹果套袋时，最好选择树冠呈现纺锤性且通风透气的植物，有利于苹果健康生长。"
	}, {
		id: 3,
		title: "预防害虫",
		description: "苹果的主要害虫有食心虫，在给苹果套袋后，可以避免害虫钻入果实内部，养殖苹果时，最好在每年的6月份进行套袋，解袋时间在每年的9月下旬至10月上旬，避免在高温或者雨天里解袋，以免苹果发黑腐烂。"
	}, {
		id: 4,
		title: "养殖方法",
		description: "养殖苹果时，需要将其栽种在向阳且土层深厚的肥沃土壤中，并在苹果树的生长期间，要为其提供腐熟的有机肥料，使苹果树健康生长，而且在苹果树花果期时，要为其疏花疏果，使植株的果实质量提高。"
	}])
	const scrolltolower = () => {
		console.log('触底了')
	}
</script>

<style lang="scss">
	.application {
		position: relative;
		width: 100%;
		min-height: 100%;

		.search {
			padding: 27rpx 17rpx;
		}
	}
</style>