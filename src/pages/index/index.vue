<template>
	
	<!-- 轮播图 -->
	<view class="u-wrap">

		<swiper class="swipper-container" circular :indicator-dots="indicatorDots" :indicator-color='indictorColor'
			:autoplay="autoplay" :interval="interval" :duration="duration">
			<swiper-item v-for="(item,index) in swipperList">
				<image class="imgs" :src='item.image' mode="aspectFil">
				</image>
			</swiper-item>
		</swiper>


<!-- 搜索框 -->
<view class="tab-strickt">
	<u-search bg-color="#FFF" margin="8px" style="flex-grow:1;"
	:show-action="true"  action-text="搜索" :animation="true"></u-search>
	
	
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
		price:75,
		title:'手機',
		image:'/static/11.jpg',
	},
	
	{
		price:385,
		title:'筆記本電腦',
		image:'/static/22.jpeg',
	},
	{
		price:784,
		title:'耳機',
		image:'/static/33.jpeg',
	},
	{
		price:7891,
		title:'手錶',
		image:'/static/44.jpg',
	},
	{
		price:2341,
		title:'養生壺',
		image:'/static/66.jpeg',
	},
	{
		price:2375,
		title:'手錶',
		image:'/static/55.jpg',
	},
	{
		price:2341,
		title:'電腦',
		image:'/static/22.jpg',
	},
	
		
	
	
	])

	// 轮播图数据

	const swipperList = ref([{
			image: '/static/swipper1.jpg'
		},
		{
			image: '/static/swipper2.jpg'
		},
		{
			image: '/static/swipper3.jpg'
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
	.tab-strickt{
		position:sticky;
		z-index:99;
		top:0;
		left:0;
		diplay:flex;
		align-items:center;
		background:#f2f2f2;
	}
</style>
