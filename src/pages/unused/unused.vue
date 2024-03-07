<template>
	<view class="u-wrap">
		<!--搜索框-->
		<u-search margin="20rpx 0rpx" :show-action="true" action-text="搜索" :animation="true"></u-search>
		<!--分类-->
		<view class="tab-strickt">
			<u-tabs active-color="#FF7670" name="cate_name" count="cate_count" :list="tabList" :is-scroll="true"
			v-model="current" @change="change"></u-tabs>
		</view>
		
		<!--瀑布流-->		
		<view class="wrap">
				<u-waterfall v-model="flowList" ref="uWaterfall">
					<template v-slot:left="{leftList}">
						<view class="demo-warter-left" v-for="(item, index) in leftList" :key="index">
							<!-- 警告：微信小程序不支持嵌入lazyload组件，请自行如下使用image标签 -->							
							<u-lazy-load threshold="-450" border-radius="10" :image="item.image" :index="index"></u-lazy-load>																					
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
							<!-- 微信小程序无效，因为它不支持在template中引入组件 -->
							<u-icon name="close-circle-fill" color="#fa3534" size="34" class="u-close" @click="remove(item.id)"></u-icon>
						</view>
					</template>
					
					<template v-slot:right="{rightList}">
						<view class="demo-warter-right" v-for="(item, index) in rightList" :key="index">					
							<u-lazy-load threshold="-450" border-radius="10" :image="item.image" :index="index"></u-lazy-load>																												
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
							<!-- 微信小程序无效，因为它不支持在template中引入组件 -->
							<u-icon name="close-circle-fill" color="#fa3534" size="34" class="u-close" @click="remove(item.id)"></u-icon>
						</view>
					</template>
				</u-waterfall>
				<u-loadmore bg-color="rgb(240, 240, 240)" :status="loadStatus" @loadmore="addRandomData"></u-loadmore>
			</view>
		
	</view>
</template>

<script setup>
	import{
		ref
	} from 'vue';
	const tabList = ref([{
		cate_name:'全部'
	},{
		cate_name:'手机'
	},{
		cate_name:'电脑'
	},{
		cate_name:'衣服'
	},{
		cate_name:'鞋子'
	},{
		cate_name:'图书'
	},{
		cate_name:'时尚'
	},{
		cate_name:'手作'
	}])
	const current = ref(0)	
	
	//瀑布流
	const flowList = ref([{
		price:75,
		title:'手机',
		image:'/static/11.jpg',		
	},
	{
			price:385,
			title:'笔记本电脑',
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
			price:2342,
			title:'手錶',
			image:'/static/55.jpg',
		},
		{
			price:2341,
			title:'手机',
			image:'/static/11.jpg',
		},
		{
			price:2341,
			title:'電腦',
			image:'/static/22.jpeg',
		},				
	])
	
</script>

<style lang="scss">
	//固定分类导航到顶部
	.tab-strickt{
		position: sticky;
		z-index: 99;
		top:0;
		left: 0;
	}
//瀑布流
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
		;
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
	}

	.demo-tag {
		display: flex;
		margin-top: 5px;
	}

	.demo-tag-owner {
		background-color: #fa3534;
		color: #FFFFFF;
		display: flex;
	}

	.demo-tag-text {
		border: 1px solid #2979ff;
		color: #2979ff;
		margin-left: 10px;
		border-radius: 50rpx;
		line-height: 1;
		padding: 4rpx 14rpx;
		display: flex;
		align-items: center;
		border-radius: 50rpx;
		font-size: 20rpx;
	}

	.demo-price {
		font-size: 30rpx;
		color: #fa3534;
		margin-top: 5px;
	}

	.demo-shop {
		font-size: 22rpx;
		color: #909399;
		margin-top: 5px;
	}
</style>
