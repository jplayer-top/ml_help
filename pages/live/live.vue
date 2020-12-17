<template>
	<view class="bg">
		<view style=" z-index: 999; position: fixed; width: 100%; height: 60px;top: 0%; background: rgb(0,0,0,0.9);">
			<view style="width: 100%;margin-top: 5px; height: 50px;display: -webkit-flex; display: flex;align-items: center; justify-content: center;">
				<text @click="toLive" style="border-radius: 45px;font-size: 14px;color: #fff; align-items: center;justify-content: center;  height: 35px; display: flex; width: 30%; background-color: #F0AD4E;text-align: center;">前往直播间</text>
				<view style="width: 20%;"></view>
				<text @click="toDownlaod" style="border-radius: 45px;font-size: 14px;color: #fff; align-items: center;justify-content: center;  height: 35px; display: flex; width: 30%; background-color: #f0aaaa;text-align: center;">未安装去下载</text>
			</view>
		</view>
		<view :style="'height:' + screenHeight + 'px !important; '">
			<video  muted autoplay="true" style="top: 10%; width: 100%; height: 90%;" src="http://www.miaogong.ltd/0f636a85-ed52-4af8-aec1-a3844230bcf2b6011294582027267462b6ed9be07aee"
			 loop="false" x5-playsinline="" playsinline="true" webkit-playsinline="true" x-webkit-airplay="true"
			 x5-video-player-type="h5" x5-video-player-fullscreen="" x5-video-orientation="portraint" controls="false"
			 :danmu-list="danmuList" enable-danmu>
			</video>
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
				danmuList: [{
						text: '我已就位',
						color: '#0000ff',
						time: 1
					},
					{
						text: '我已就位',
						color: '#ffff00',
						time: 2
					}, {
						text: '我已就位',
						color: '#ff0000',
						time: 3
					}, {
						text: '我已就位',
						color: '#ffffff',
						time: 4
					},
					{
						text: '我已就位',
						color: '#ffffff',
						time: 5
					},
					{
						text: '我已就位',
						color: '#112322',
						time: 6
					}, {
						text: '我已就位',
						color: '#ffffff',
						time: 7
					}, {
						text: '我已就位',
						color: '#ffffff',
						time: 8
					}, {
						text: '秒乐加油',
						color: '#ffffff',
						time: 9
					},
					{
						text: '我已就位',
						color: '#ffffff',
						time: 10
					},
					{
						text: '我已就位',
						color: '#ffffff',
						time: 11
					}, {
						text: '我已就位',
						color: '#ffffff',
						time: 12
					}, {
						text: '我已就位',
						color: '#ffffff',
						time: 13
					}
				],
				shortId: '',
				shareUser: '',
				screenHeight: 0,
				showMaskWx: false,
				title: 'Hello'
			}
		},
		onLoad() {
			this.shortId = this.getUrlParam('shortId');
			this.shareUser = this.getUrlParam('shareUser');
			this.showMaskWx = this.isWeiXin()
			this.screenHeight = uni.getSystemInfoSync().windowHeight;
		},
		methods: {
			getUrlParam(name) {
				var reg = new RegExp("(^|&)" + name + "=([^&]*)(&|$)"); //构造一个含有目标参数的正则表达式对象
				var r = location.href.split("?")[1].match(reg); //匹配目标参数
				if (r != null) return decodeURI(r[2]);
				return null; //返回参数值
			},
			toLive() {
				// uni.showToast({
				// 	duration:2000,
				// 	title:this.shortId
				// })
				window.location = 'jplayer://liveloading?shortId=' + this.shortId+"&shareUser=" + this.shareUser;
			},
			toDownlaod() {
				// window.location = 'https://a.app.qq.com/o/simple.jsp?pkgname=top.jplayer.jpvideo&g_f=1000047';
				uni.navigateTo({
					url: '/pages/download/download',
				});
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
