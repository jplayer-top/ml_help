<template>
		<view class="bg" >
			<view :style="'height:' + screenHeight + 'px !important; '">
				<image style="width: 100%; height: 100%;" src="../../static/webp.png"  @click="toDownlaod"></image>
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
		this.showMaskWx =this.isWeiXin()
		this.screenHeight = uni.getSystemInfoSync().windowHeight;
	},
	methods: {
		toDownlaod(){
			// window.location = 'https://a.app.qq.com/o/simple.jsp?pkgname=top.jplayer.jpvideo&g_f=1000047';
			window.location = 'http://apk.miaogong.xyz/kx5z';
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
};
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
		
	}
	.image {
		width: 100%;
		height: 100%;
		background: white;
		position: fixed;
	}
</style>
