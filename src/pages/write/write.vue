<template>
	<view class="u-wrap u-p-l-20 u-p-r-20" >
		<u-form :model="addModel" ref="form1">
					<u-form-item label="类型:">
						<u-radio-group v-model="addModel.type">
							<u-radio activeColor="#oocc33" v-for="(item, index) in list" :key="index" :name="item.name" :disabled="item.disabled">
								{{ item.name }}
							</u-radio>
						</u-radio-group>
					</u-form-item>
					<u-form-item label="名称:">
						<u-input placeholder="请输入名称" v-model="addModel.title" />
					</u-form-item>
					<u-form-item label="简介:">
						<u-input placeholder="请输入简介" v-model="addModel.introduce" />
					</u-form-item>
					<u-form-item label="价格:">
						<u-input placeholder="请输入价格" v-model="addModel.price" />
					</u-form-item>
					<u-form-item label-width="auto" label="联系人:">
						<u-input placeholder="请输入联系人" v-model="addModel.userName" />
					</u-form-item>
					<u-form-item label-width="auto" label="联系电话:">
						<u-input placeholder="请输入联系电话" v-model="addModel.phone" />
					</u-form-item>
					<u-form-item label="图片:"></u-form-item>
					<u-upload :action="action" :file-list="filelist"></u-upload>
				</u-form>
				<u-button :custom-style="customStyle">发布</u-button>
	</view>
</template>

<script setup>
	import{
		reactive,
		ref
	} from 'vue';
	const addModel = reactive({
		type: '',
		title: '',
		introdeuce: '',
		price: '',
		userName: '',
		phone: '',
		image: '',
	})
	
	const list = [{
		name: '闲置',
		disabled: false
	},
	{
		name: '求购',
		disabled: false
	},
	]
	
	const value = ref('')
	const action = ref('')
	const fileList = ref([])
	
	const customStyle = reactive({
		background: '#00cc33',
		color: '#FFF',
		marginTop: '15px',
		width: '100%'
	})
</script>

<style>

</style>
