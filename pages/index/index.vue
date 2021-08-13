<template>
	<view class="content">
		<view class="time1">
			<view class="item" @tap="dateVisible1=true">日期1</view>
			<w-picker :visible.sync="dateVisible1" mode="date" startYear="2017" endYear="2029"
				value="2020-04-08 16:45:45" :current="false" fields="second" @confirm="onConfirm($event,'date1')"
				@cancel="onCancel" :disabled-after="false" ref="date1"></w-picker>
			<view class="result">选择结果：{{result}}</view>
		</view>
		<view class="time1" style="margin-top: 20px;">
			<view class="item" @tap="dateVisible2=true">日期2</view>
			<w-picker :visible.sync="dateVisible2" mode="date" startYear="2017" endYear="2029"
				value="2020-04-08 16:45:45" :current="false" fields="second" @confirm="onConfirm2($event,'date2')"
				@cancel="onCancel" :disabled-after="false" ref="date2"></w-picker>
			<view class="result">选择结果：{{result2}}</view>
		</view>
		<view class="dq" style="margin-top: 20px;">
			<view class="item" @tap="regionVisible=true">省市区三级联动</view>
			<view class="result">选择结果：{{dq}}</view> 
			<w-picker
				:visible.sync="regionVisible"
				mode="region"
				:value="defaultRegion"
				default-type="value"
				:hide-area="false"
				@confirm="onConfirm3($event,'region')"
				@cancel="onCancel"
				ref="region" 
			></w-picker>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				dateVisible1: false,
				dateVisible2: false, 
				result: '',
				result2: '',
				dq:'',
				regionVisible:false,
				defaultRegion:["150000","150100","150103"]
			}
		},
		onLoad() {

		},
		methods: {
			// 日期1
			onConfirm(res) {
				this.result = res.result;
				console.log(res)
			},
			onCancel() {

			},
			// 日期2
			onConfirm2(res) {
				console.log('a')
				this.result2 = res.result;
				console.log(res)
			},
			onCancel() {
			
			},
			// 地区
			onConfirm3(res){
				console.log('onConfirm3')
				this.dq=res.result;
				console.log(res)
			},
			onCancel(){
				
			}
		}
	}
</script>

<style>
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}

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
		justify-content: center;
	}

	.title {
		font-size: 36rpx;
		color: #8f8f94;
	}
</style>
