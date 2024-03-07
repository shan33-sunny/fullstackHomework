<template>

	<!-- 轮播图 -->
	<view class="u-wrap">

		<swiper class="swipper-container" circular :indicator-dots="indicatorDots" :indicator-color='indictorColor'
			:autoplay="autoplay" :interval="interval" :duration="duration">
			<swiper-item v-for="(item,index) in swipperList" :key="index">
				<image class="imgs" :src="item.image" mode="aspectFill"></image>
			</swiper-item>
		</swiper>


		<!-- 搜索框 -->
		<view class="tab-strickt">
			<u-search bg-color="#FFF" margin="8px" style="flex-grow:1;" :show-action="true" action-text="搜索"
				:animation="true"></u-search>


		</view>
		<!--瀑布流-->



		<view class="">
			<u-waterfall v-model="flowList" ref="uWaterfall">

				<template v-slot:left="{leftList}">
					<view class="demo-warter-left" v-for="(item,index) in leftList" :key="index">
						<u-lazy-load threshold="-450" border-radius="10" :image="item.image" :index="index">

						</u-lazy-load>


						<view class="demo-title">
							{{item.title}}
						</view>
						<view class="demo-price">
							{{item.price}}元
						</view>
						<view class="demo-tag">
							<view class="demo-tag-owner">
								自营
							</view>
							<view class="demo-tag-text">
								放心购
							</view>
						</view>
						<view class="demo-shop">
							{{item.shop}}
						</view>
						<u-icon name="close-circle-fill" color="#fa3534" size="34" class="u-close"
							@click="remove(item.id)">
						</u-icon>
					</view>
				</template>

				<template v-slot:right="{rightList}">
					<view class="demo-warter-right" v-for="(item,index) in rightList" :key="index">
						<u-lazy-load threshold="-450" border-radius="10" :image="item.image" :index="index">

						</u-lazy-load>

						<view class="demo-title">
							{{item.title}}
						</view>
						<view class="demo-price">
							{{item.price}}元
						</view>
						<view class="demo-tag">
							<view class="demo-tag-owner">
								自营
							</view>
							<view class="demo-tag-text">
								放心购
							</view>
						</view>
						<view class="demo-shop">
							{{item.shop}}
						</view>
						<u-icon name="close-circle-fill" color="#fa3534" size="34" class="u-close"
							@click="remove(item.id)">
						</u-icon>

					</view>
				</template>
			</u-waterfall>
			<u-loadmore bg-color="rgb(240,240,240)" :status="loadStatus" @loadmore="addRandomDate"></u-loadmore>

		</view>



	</view>
</template>

<script setup>
	// 1、引用ref模版
	import {
		ref
	} from 'vue';

	// 2.响应式数据
	const indicatorDots = ref(true)
	const indicatorColor = ref("#FFF")
	const autoplay = ref(true)
	const interval = ref(20000)
	const duration = ref(500)

	// 瀑佈流
	const flowList = ref([{
			price: 75,
			title: '手機',
			image: '/static/11.jpg',
		},

		{
			price: 385,
			title: '筆記本電腦',
			image: '/static/11.jpeg',
		},
		{
			price: 784,
			title: '耳機',
			image: '/static/33.jpeg',
		},
		{
			price: 7891,
			title: '手錶',
			image: '/static/44.jpg',
		},
		{
			price: 2341,
			title: '養生壺',
			image: '/static/66.jpeg',
		},
		{
			price: 2342,
			title: '手錶',
			image: '/static/55.jpg',
		},
		{
			price: 2341,
			title: '手机',
			image: '/static/11.jpg',
		},
		{
			price: 2341,
			title: '電腦',
			image: '/static/22.jpg',
		},





	])

	// 轮播图数据

	const swipperList = ref([{
			image: '/static/33.jpg'
		},
		{
			image: '/static/44.jpg'
		},
		{
			image: '/static/66.jpg'
		},
	])
</script>

<style lang="scss">
	.swipper-container {
		height: 220px;

		.item {
			height: 220px;
		}
	}

	.imgs {
		height: 220ps;
		width: 100%;
	}


	// 搜索框
	.tab-strickt {
		position: sticky;
		z-index: 99;
		top: 0;
		left: 0;
		display: flex;
		align-items: center;
		background: #f2f2f2;
	}

	// 瀑布流
	
	.demo-warter-left {
	  border-radius: 8px;
	  margin: 5px 0px 5px 5px;
	  background-color: #ffffff;
	  padding: 8px;
	  position: relative;
	}
	
	.demo-warter-right {
	  border-radius: 8px;
	  margin: 5px 5px 5px 0px;
	  background-color: #ffffff;
	  padding: 8px;
	  position: relative;
	}
	
	.u-close {
	  position: absolute;
	  top: 32rpx;
	  right: 32rpx;
	}
	
	.demo-image {
	  width: 100%;
	  border-radius: 4px;
	}
	
	.demo-title {
	  font-size: 30rpx;
	  margin-top: 5px;
	  color: $u-main-color; // 修改为直接颜色值，移除$u-main-color
	}
	.demo-tag{
		display: flex;
		
	}
	
	.demo-tag-owner {
	  background-color: $u-type-error; // 移除$u-type-error
	  color: #ffffff;
	  display: flex;
	}
	
	.demo-tag-text {
	  border: 1px solid $u-type-primary; // 移除$u-type-primary
	  color: $u-type-primary; // 移除$u-type-primary
	  margin-left: 10px;
	  border-radius: 50rpx;
	  line-height: 1;
	  padding: 4rpx 14rpx;
	  display: flex;
	  align-items: center;
	  font-size: 20rpx;
	}
	
	.demo-price {
	  font-size: 30rpx;
	  color: #fa3534; // 修改为直接颜色值，移除$u-type-error
	  margin-top: 5px;
	}
	
	.demo-shop {
	  font-size: 22rpx;
	  color: #909399; // 修改为直接颜色值，移除$u-tips-color
	  margin-top: 5px;
	}
</style>
