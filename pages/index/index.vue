<template>
		<view class="bg" >
			<view :style="'height:'+ screenHeight +'px !important; '" >
				<image @click="onApp" mode="widthFix" src="../../static/pic.png" style="width: 80%; margin-left: 10%; margin-top: 30%;"></image>
			</view>
		
			<view v-if="showMaskWx" class="maskWx">
			      <view>
			        <image src="../../static/MASK.png" class="image_mask">
			      </view>
			</view>
		</view>
</template>

<script>
	export default {
		data() {
			return {
				shortId:'',
				screenHeight:0,
				showMaskWx:false,
				title: 'Hello'
			}
		},
		onLoad() {
			this.screenHeight = uni.getSystemInfoSync().windowHeight;
			this.showMaskWx =this.isWeiXin()
			console.log(this.showMaskWx,'------------')
			this.shortId = this.getUrlParam('shortId');
		},
		methods: {
			getUrlParam(name) {
			  var reg = new RegExp("(^|&)" + name + "=([^&]*)(&|$)"); //构造一个含有目标参数的正则表达式对象
			  var r = location.href.split("?")[1].match(reg);  //匹配目标参数
			  if (r != null) return decodeURI(r[2]); return null; //返回参数值
			},
			onApp(){
				// uni.showToast({
				// 	duration:2000,
				// 	title:this.shortId
				// })
				window.location = 'jplayer://helploading?shortId=' + this.shortId;
			},
			isWeiXin() {
				var ua = window.navigator.userAgent.toLowerCase();
				if (ua.match(/MicroMessenger/i) == 'micromessenger') {
					return true;
				} else {
					return false;
			}
		},
		}
	}
</script>

<style >
	
	.maskWx {
		position: fixed;
		width: 100%;
		height: 100%;
		background: rgba(0, 0, 0, 0.41);
		left: 0;
		z-index: 10000;
		top: 0;
	}
	.image_mask {
		width: 200rpx;
		position: absolute;
		right: 3%;
		height: 80rpx;
	}
	.bg {
		background: #333333;
	}
	.image {
		width: 100%;
		height: 100%;
		background: white;
		position: fixed;
	}
</style>
