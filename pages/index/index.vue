<template>
		<view class="bg" >
			<view :style="'height:'+ screenHeight +'px !important; '" >
				<a href="jplayer://helploading?id=10000">open android app</a>
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
				screenHeight:0,
				showMaskWx:false,
				title: 'Hello'
			}
		},
		onLoad() {
			this.screenHeight = uni.getSystemInfoSync().windowHeight;
			this.showMaskWx =this.isWeiXin()
			console.log(this.showMaskWx,'------------')
			
		},
		methods: {
			onApp(){
				window.location = 'jplayer://helploading?id=10000';
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

<style>
	
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
		.image {
			width: 100%;
			height: 100%;
			background: white;
			position: fixed;
		}
	}
</style>
