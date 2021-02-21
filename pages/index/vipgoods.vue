<template>
		<view class="bg" >
			<view :style="'height:'+ screenHeight +'px !important; '" >
				<image  mode="widthFix" src="../../static/goods_vip.png" style="width: 80%; margin-left: 10%; margin-top: 10%;"></image>
				
				<button @click="onApp" style="border-radius: 45px; background-color: #3F536E;color: #ffffff; margin-top: 50rpx; width: 80%; margin-left: 10%;font-size: 13px;padding: 6px;">已安装，去购买</button>
				<button @click="onDownload" style="border-radius: 45px; background-color: #DD524D;color: #ffffff; margin-top: 50rpx; width: 80%; margin-left: 10%;font-size: 13px;padding: 6px;">未安装，去下载</button>
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
			this.goodsId = this.getUrlParam('goodsId');
			console.log(this.shortId,this.goodsId)
		},
		methods: {
			getUrlParam(name) {
			  var reg = new RegExp("(^|&)" + name + "=([^&]*)(&|$)"); //构造一个含有目标参数的正则表达式对象
			  var r = location.href.split("?")[1].match(reg);  //匹配目标参数
			  if (r != null) return decodeURI(r[2]); return null; //返回参数值
			},
			onDownload(){
				  uni.navigateTo({
				       url: '/pages/download/download',
				          });
			},
			onApp(){
				// uni.showToast({
				// 	duration:2000,
				// 	title:this.shortId
				// })
				window.location = 'jplayer://vipgoods?shortId=' + this.shortId+"&goodsId="+ this.goodsId;
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
