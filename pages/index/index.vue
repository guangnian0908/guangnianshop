<template>
	<view class="content">
		<swiper indicator-dots circular>
			<swiper-item v-for="item in swipers" :key="item.goods_id">
				<image mode="widthFix" :src="item.image_src"></image>
			</swiper-item>
		</swiper>
		<input type="text" placeholder-style="color:#cccccc;" style="width: 50%;height: 30rpx; border: 1rpx solid #007AFF;" :value="123123"/>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				swipers: []
			}
		},
		onLoad() {
			this.getSwipers()
		},
		methods: {
			// 获取轮播图的数据
			async getSwipers() {
				const res = await this.$myRuquest({
					url: '/api/public/v1/home/swiperdata'
				})
				this.swipers = res.data.message
			},

		}
	}
</script>

<style lang="less">
	.content {
		swiper {
			width: 750rpx;
			height: 350rpx;
			image {
				width: 100%;
				height: 100%;
			}
		}
	}
</style>
