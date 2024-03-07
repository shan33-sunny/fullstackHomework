<template>
	<view class="u-p-t-40 u-p-r-60 u-p-b-30 u-p-l-60 logincontainer">
		<button class="avatarwrap" open-type="chooseAvatar" bind:chooseavatar="onChooseAvatar">
			<image class="avatar" :src="avatarUrl"></image>		
		</button>
		<u-form class="forms" :model="loginModel" ref="form1">
		            <u-form-item left-icon="phone-fill" left-icon-style="font-size:24px;color:#FF7670;">
		                <u-input placeholder="请输入电话" v-model="loginModel.phone" />
		            </u-form-item>
		            <u-form-item left-icon="account-fill" left-icon-style="font-size:24px;color:#FF7670;">
		                <u-input placeholder="请输入账户" v-model="loginModel.phone" />
		            </u-form-item>
					<u-form-item left-icon="lock" left-icon-style="font-size:24px;color:#FF7670;">
					    <u-input placeholder="请输入密码" v-model="loginModel.phone" />
					</u-form-item>
					<u-form-item left-icon="lock" left-icon-style="font-size:24px;color:#FF7670;">
					    <u-input placeholder="请输入确定密码" v-model="loginModel.passwordConfirm" />
					</u-form-item>
		            <view class="passtext">
		                已有账号，去登录
		            </view>
		            
		            <!-- 按钮 -->
		            <u-button type="success" :custom-style="customStyle1">注册</u-button>
		        </u-form>
	</view>
</template>

<script setup>
	import{
		ref,
	    reactive
	} from 'vue';
	
	const onChooseAvatar = (e) => {}
	
	const avatarUrl = ref('/static/user.jpg')
	
	const loginModel = reactive({
		phone: '',
		username: '',
		password: '',
		passwordConfirm: ''
	})
	
	const customStyle1 = reactive({
		marginTop: '40px',
		color: '#FFF',
		width: '100%'
	})
</script>

<style lang="scss">
	.avatarwrap{
		border-radius: 100%;
		display: flex;
		justify-content: center;
		align-items: center;
		height: 70px;
		width: 70px;
		padding: 0px;
		
		.avatar {
			border-radius: 100%;
			height: 70px;
			width: 70px;
		}
	}
    .passtext{
		display: flex;
		justify-content: flex-end;
		color: #FF7670;
		margin-top: 15px;
	}
</style>
