<template>
    <view  class="u-p-40 u-p-r-60 u-p-b-30 u-p-l-60 logincontainer">
        <!-- 头像 -->
        <u-avatar size="140" src="/static/logo.png" mode="circle"></u-avatar>
        
        <!-- 表单 -->
        <u-form class="form" :model="loginModel" ref="form1">
            <u-form-item left-icon="account-fill" left-icon-style="font-size:24px;color:#FF7679">
                <u-input placeholder="请输入账号" v-model="loginModel.username"></u-input>
            </u-form-item>
            <u-form-item left-icon="lock" left-icon-style="font-size:24px;color:#FF7670">
                <u-input placeholder="请输入密码" v-model="loginModel.password"></u-input>
            </u-form-item>
            <view class="passtext">
                忘记密码
            </view>
            
            <!-- 按钮 -->
            <u-button :custom-style="customStyle1"> 登录</u-button>
            <u-button type="success" :custom-style="customStyle2">注册</u-button>
        </u-form>
    </view>
</template>

<script setup>
   import{
	   reactive
   }from 'vue'
   
   
   // 表单数据
   const loginModel = reactive({
	   username:'',
	   password:'',
   })
   // 登录按钮

const customStyle1 = reactive({
    marginTop: '40px',
    background: '#FF7679',
    color: '#FFF',
    width: '100%'
});
   // 注册按钮
   const customStyle2 = reactive({
   	   marginTop:'35px',
   	   color:'#FFF',
   	   width:'100%'
   })
</script>

<style lang="scss">
    .logincontainer {
        height: 100%;
        display: flex;
        align-items: center;
        flex-direction: column;
    }
	
	// 表单
	.forms{
		width: 100%;
		margin-top: 30px;
	}
	// 忘记密码
	.passtext{
		display: flex;
		justify-content: flex-end;
		color: #FF7670;
		margin-top: 15px;
	}
</style>
