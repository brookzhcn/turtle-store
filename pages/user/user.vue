<template>
	<view class="container">

		<view class="user-section">
			<image class="bg" src="/static/user-bg.jpg"></image>
			<view class="user-info-box">
				<view class="portrait-box">
					<image class="portrait" :src="userInfo.portrait || '/static/missing-face.png'" @click="checkLogin"></image>
				</view>
				<view class="info-box">
					<text class="username">{{userInfo.nickname || '游客'}}</text>
				</view>
			</view>
			<view class="vip-card-box">
				<image class="card-bg" src="/static/vip-card-bg.png" mode=""></image>
				<view class="b-btn">
					立即开通
				</view>
				<view class="tit">
					<text class="yticon icon-iLinkapp-"></text>
					乌龟企业会员
				</view>
				<text class="e-m">Turtle Union</text>
				<text class="e-b">绑定企业会员，即可享受企业专属福利</text>
			</view>
		</view>

		<view class="cover-container" :style="[{
				transform: coverTransform,
				transition: coverTransition
			}]"
		 @touchstart="coverTouchstart" @touchmove="coverTouchmove" @touchend="coverTouchend">
			<image class="arc" src="/static/arc.png"></image>

			<view class="tj-sction">
				<view class="tj-item">
					<text class="num">128.8</text>
					<text>余额</text>
				</view>
				<view class="tj-item">
					<text class="num">0</text>
					<text>优惠券</text>
				</view>
				<view class="tj-item">
					<text class="num">20</text>
					<text>积分</text>
				</view>
			</view>
			<!-- 订单 -->
			<view class="order-section">
				<view class="order-item" @click="navTo('/pages/order/order?state=0')" hover-class="common-hover" :hover-stay-time="50">
					<text class="yticon icon-shouye"></text>
					<text>全部订单</text>
				</view>
				<view class="order-item" @click="navTo('/pages/order/order?state=1')" hover-class="common-hover" :hover-stay-time="50">
					<text class="yticon icon-daifukuan"></text>
					<text>待付款</text>
				</view>
				<view class="order-item" @click="navTo('/pages/order/order?state=2')" hover-class="common-hover" :hover-stay-time="50">
					<text class="yticon icon-yishouhuo"></text>
					<text>待收货</text>
				</view>
				<view class="order-item" @click="navTo('/pages/order/order?state=4')" hover-class="common-hover" :hover-stay-time="50">
					<text class="yticon icon-shouhoutuikuan"></text>
					<text>退款/售后</text>
				</view>
			</view>
			<!-- 浏览历史 -->
			<view class="history-section icon">
				<view class="sec-header">
					<text class="yticon icon-lishijilu"></text>
					<text>浏览历史</text>
				</view>
				<scroll-view scroll-x class="h-list">
					<image @click="navTo('/pages/product/product')" src="https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1553105186633&di=c121a29beece4e14269948d990f9e720&imgtype=0&src=http%3A%2F%2Fimg004.hc360.cn%2Fm8%2FM04%2FDE%2FDE%2FwKhQplZ-QteEBvsbAAAAADUkobU751.jpg"
					 mode="aspectFill"></image>
					<image @click="navTo('/pages/product/product')" src="https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1553105231218&di=09534b9833b5243296630e6d5b728eff&imgtype=0&src=http%3A%2F%2Fimg002.hc360.cn%2Fm1%2FM05%2FD1%2FAC%2FwKhQcFQ3iN2EQTo8AAAAAHQU6_8355.jpg"
					 mode="aspectFill"></image>
					<image @click="navTo('/pages/product/product')" src="https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1553105320890&di=c743386be51f2c4c0fd4b75754d14f3c&imgtype=0&src=http%3A%2F%2Fimg007.hc360.cn%2Fhb%2FMTQ1OTg4ODY0MDA3Ny05OTQ4ODY1NDQ%3D.jpg"
					 mode="aspectFill"></image>
					<image @click="navTo('/pages/product/product')" src="https://ss2.bdstatic.com/70cFvnSh_Q1YnxGkpoWK1HF6hhy/it/u=2691146630,2165926318&fm=26&gp=0.jpg"
					 mode="aspectFill"></image>
					<image @click="navTo('/pages/product/product')" src="https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1553105443324&di=8141bf13f3f208c61524d67f9bb83942&imgtype=0&src=http%3A%2F%2Fimg.zcool.cn%2Fcommunity%2F01ac9a5548d29b0000019ae98e6d98.jpg"
					 mode="aspectFill"></image>
					<image @click="navTo('/pages/product/product')" src="https://ss0.bdstatic.com/70cFuHSh_Q1YnxGkpoWK1HF6hhy/it/u=191678693,2701202375&fm=26&gp=0.jpg"
					 mode="aspectFill"></image>
				</scroll-view>
				<list-cell icon="icon-iconfontweixin" iconColor="#e07472" title="我的钱包" tips="您的会员还有3天过期"></list-cell>
				<list-cell icon="icon-dizhi" iconColor="#5fcda2" title="地址管理" @eventClick="navTo('/pages/address/address')"></list-cell>
				<!--  #ifndef  MP-WEIXIN -->
				<list-cell icon="icon-share" iconColor="#9789f7" title="分享" tips="邀请好友赢10万大礼">
				</list-cell>
				<!--  #endif -->
				<list-cell icon="icon-pinglun-copy" iconColor="#ee883b" title="晒单" tips="晒单抢红包"></list-cell>
				<list-cell icon="icon-shoucang_xuanzhongzhuangtai" iconColor="#54b4ef" title="我的收藏" @eventClick="navTo('/pages/collection/collection')"></list-cell>
				<list-cell icon="icon-shezhi1" iconColor="#e07472" title="设置" border="" @eventClick="navTo('/pages/set/set')"></list-cell>
				<list-cell uniIconType="phone-filled" uniIconSize="21"  iconColor="#eb507e" title="绑定手机号" border="" @eventClick="navTo('/pages/authorize/authorize')"></list-cell>
				<list-cell uniIconType="chat" uniIconSize="18" iconColor="#eb507e" title="意见反馈" border="" @eventClick="navTo('/pages/feedback/feedback')"></list-cell>
				<list-cell uniIconType="scan" uniIconSize="19"  iconColor="#eb507e" title="扫一扫" border="" @eventClick="navTo('/pages/scan/scan')"></list-cell>
				<list-cell uniIconType="compose" uniIconSize="21"  iconColor="#eb507e" title="申请开票" border="" @eventClick="navTo('/pages/invoice/invoice')"></list-cell>
				<list-cell uniIconType="bars" uniIconSize="21"  iconColor="#eb507e" title="开票记录" border="" @eventClick="navTo('/pages/invoice/list')"></list-cell>
				<!-- <list-cell uniIconType="info" uniIconSize="20"  iconColor="#eb507e" title="充值" border="" @eventClick="navTo('/pages/recharge/recharge')"></list-cell> -->
				<list-cell uniIconType="help" uniIconSize="20"  iconColor="#eb507e" title="关于我们" border="" @eventClick="aboutUs"></list-cell>
				<list-cell uniIconType="phone" uniIconSize="20"  iconColor="#eb507e" title="联系客服" border="" @eventClick="makePhoneCall"></list-cell>
				<list-cell uniIconType="spinner-cycle" uniIconSize="20"  iconColor="#eb507e" title="生成二维码" border="" @eventClick="navTo('/pages/qrcode/qrcode')"></list-cell>
				<!-- <list-cell uniIconType="compose" uniIconSize="20"  title="签到" border="" @eventClick="navTo('/pages/sign/sign')"></list-cell> -->
				<!-- <list-cell uniIconType="list" uniIconSize="21"  iconColor="#eb507e" title="开票记录" border="" @eventClick="navTo('/pages/invoice/list')"></list-cell> -->
				
			</view>
		</view>
		
	</view>
</template>
<script>
	import listCell from '@/components/mix-list-cell';
	import uniIcon from "@/components/uni-icon/uni-icon.vue";
	import {
		mapState
	} from 'vuex';
	let startY = 0,
		moveY = 0,
		pageAtTop = true;
	export default {
		components: {
			listCell,
			uniIcon,
		},
		data() {
			return {
				coverTransform: 'translateY(0px)',
				coverTransition: '0s',
				moving: false,
				servicePhoneNumber: '18851070553',
			}
		},
		onLoad() {},
		// #ifndef MP
		onNavigationBarButtonTap(e) {
			const index = e.index;
			if (index === 0) {
				this.navTo('/pages/set/set');
			} else if (index === 1) {
				// #ifdef APP-PLUS
				const pages = getCurrentPages();
				const page = pages[pages.length - 1];
				const currentWebview = page.$getAppWebview();
				currentWebview.hideTitleNViewButtonRedDot({
					index
				});
				// #endif
				uni.navigateTo({
					url: '/pages/notice/notice'
				})
			}
		},
		// #endif
		onShareAppMessage(res) {
			if (res.from === 'button') {
				// 来自页面内转发按钮
				console.log(res.target)
			}
			return {
				title: '乌龟商店',
				path: '/pages/user/user'
			}
		},
		computed: {
			...mapState(['hasLogin', 'userInfo'])
		},
		methods: {
			aboutUs : function () {
			   wx.showModal({
			     title: '关于我们',
			     content: '本系统是由xxx开发，祝大家使用愉快！',
			     showCancel:false
			   })
			 },
			 makePhoneCall: function () {
			     var that = this;
			     wx.makePhoneCall({
			       phoneNumber: that.servicePhoneNumber,
			       success: function (res) { },
			       fail: function (res) {
			         wx.showModal({
			           title: '呼叫失败',
			           content: '请稍后再试',
			           showCancel: false,
			         })
			       },
			       complete: function (res) { },
			     })
			   },
			/**
			 * 统一跳转接口,拦截未登录路由
			 * navigator标签现在默认没有转场动画，所以用view
			 */
			navTo(url) {
				if (!this.hasLogin) {
					url = '/pages/public/login';
				}
				uni.navigateTo({
					url
				})
			},

			checkLogin(e) {
				const url = '/pages/public/login';
				if (!this.hasLogin) {
					uni.navigateTo({
						url
					});
				}

			},
			/**
			 *  会员卡下拉和回弹
			 *  1.关闭bounce避免ios端下拉冲突
			 *  2.由于touchmove事件的缺陷（以前做小程序就遇到，比如20跳到40，h5反而好很多），下拉的时候会有掉帧的感觉
			 *    transition设置0.1秒延迟，让css来过渡这段空窗期
			 *  3.回弹效果可修改曲线值来调整效果，推荐一个好用的bezier生成工具 http://cubic-bezier.com/
			 */
			coverTouchstart(e) {
				if (pageAtTop === false) {
					return;
				}
				this.coverTransition = 'transform .1s linear';
				startY = e.touches[0].clientY;
			},
			coverTouchmove(e) {
				moveY = e.touches[0].clientY;
				let moveDistance = moveY - startY;
				if (moveDistance < 0) {
					this.moving = false;
					return;
				}
				this.moving = true;
				if (moveDistance >= 80 && moveDistance < 100) {
					moveDistance = 80;
				}

				if (moveDistance > 0 && moveDistance <= 80) {
					this.coverTransform = `translateY(${moveDistance}px)`;
				}
			},
			coverTouchend() {
				if (this.moving === false) {
					return;
				}
				this.moving = false;
				this.coverTransition = 'transform 0.3s cubic-bezier(.21,1.93,.53,.64)';
				this.coverTransform = 'translateY(0px)';
			}
		}
	}
</script>
<style lang='scss'>
	%flex-center {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
	}

	%section {
		display: flex;
		justify-content: space-around;
		align-content: center;
		background: #fff;
		border-radius: 10upx;
	}

	.user-section {
		height: 520upx;
		padding: 100upx 30upx 0;
		position: relative;

		.bg {
			position: absolute;
			left: 0;
			top: 0;
			width: 100%;
			height: 100%;
			filter: blur(1px);
			opacity: .7;
		}
	}

	.user-info-box {
		height: 180upx;
		display: flex;
		align-items: center;
		position: relative;
		z-index: 1;

		.portrait {
			width: 130upx;
			height: 130upx;
			border: 5upx solid #fff;
			border-radius: 50%;
		}

		.username {
			font-size: $font-lg + 6upx;
			color: $font-color-dark;
			margin-left: 20upx;
		}
	}

	.vip-card-box {
		display: flex;
		flex-direction: column;
		color: #f7d680;
		height: 240upx;
		background: linear-gradient(left, rgba(0, 0, 0, .7), rgba(0, 0, 0, .8));
		border-radius: 16upx 16upx 0 0;
		overflow: hidden;
		position: relative;
		padding: 20upx 24upx;

		.card-bg {
			position: absolute;
			top: 20upx;
			right: 0;
			width: 380upx;
			height: 260upx;
		}

		.b-btn {
			position: absolute;
			right: 20upx;
			top: 16upx;
			width: 132upx;
			height: 40upx;
			text-align: center;
			line-height: 40upx;
			font-size: 22upx;
			color: #36343c;
			border-radius: 20px;
			background: linear-gradient(left, #f9e6af, #ffd465);
			z-index: 1;
		}

		.tit {
			font-size: $font-base+2upx;
			color: #f7d680;
			margin-bottom: 28upx;

			.yticon {
				color: #f6e5a3;
				margin-right: 16upx;
			}
		}

		.e-b {
			font-size: $font-sm;
			color: #d8cba9;
			margin-top: 10upx;
		}
	}

	.cover-container {
		background: $page-color-base;
		margin-top: -150upx;
		padding: 0 30upx;
		position: relative;
		background: #f5f5f5;
		padding-bottom: 20upx;

		.arc {
			position: absolute;
			left: 0;
			top: -34upx;
			width: 100%;
			height: 36upx;
		}
	}

	.tj-sction {
		@extend %section;

		.tj-item {
			@extend %flex-center;
			flex-direction: column;
			height: 140upx;
			font-size: $font-sm;
			color: #75787d;
		}

		.num {
			font-size: $font-lg;
			color: $font-color-dark;
			margin-bottom: 8upx;
		}
	}

	.order-section {
		@extend %section;
		padding: 28upx 0;
		margin-top: 20upx;

		.order-item {
			@extend %flex-center;
			width: 120upx;
			height: 120upx;
			border-radius: 10upx;
			font-size: $font-sm;
			color: $font-color-dark;
		}

		.yticon {
			font-size: 48upx;
			margin-bottom: 18upx;
			color: #fa436a;
		}

		.icon-shouhoutuikuan {
			font-size: 44upx;
		}
	}

	.history-section {
		padding: 30upx 0 0;
		margin-top: 20upx;
		background: #fff;
		border-radius: 10upx;

		.sec-header {
			display: flex;
			align-items: center;
			font-size: $font-base;
			color: $font-color-dark;
			line-height: 40upx;
			margin-left: 30upx;

			.yticon {
				font-size: 44upx;
				color: #5eba8f;
				margin-right: 16upx;
				line-height: 40upx;
			}
		}

		.h-list {
			white-space: nowrap;
			padding: 30upx 30upx 0;

			image {
				display: inline-block;
				width: 160upx;
				height: 160upx;
				margin-right: 20upx;
				border-radius: 10upx;
			}
		}
	}
</style>
