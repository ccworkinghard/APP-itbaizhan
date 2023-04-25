<template>
	<view class="home">
		<Navbar></Navbar>
		<view class="index_banner_box">
			<swiper class="swiper" :indicator-dots="true" :autoplay="true" :interval="3000" :duration="500">
				<swiper-item v-for="(item,index) in topBanner" :key="index">
					<image class="banner" :src="item.img_url" mode=""></image>
				</swiper-item>

			</swiper>

		</view>
		<CourseNav></CourseNav>
		<view class="online_box">
			<image :src="index_banner.img_url" class="online_img"></image>
		</view>
		<view class="free_box">
			<view class="free_T_box public_two_box">
				<view class="public_T">
					限时免费
				</view>
			</view>
			<FreeCard></FreeCard>
		</view>
		<view class="public_title">
			<view class="public_class_T">
				零基础就业班
			</view>
			<JobScroll></JobScroll>
		</view>
		<view class="recommend_box">
			<view class="recommend_T_box public_two_box">
				<view class="public_T">
					推荐课程
				</view>
			</view>
			<CourseCard></CourseCard>
		</view>
		<view class="daotu_box">
			<view class="daotu_T">
				驱动教学-贯穿教 | 学 | 练 | 测 | 评
			</view>
			<image :src="footBanner.img_url" mode=""></image>
		</view>
	</view>
</template>

<script>
	import Navbar from "../../../uni_modules/navbar/navbar.vue"
	import CourseNav from "../../../uni_modules/coursenav/coursenav.vue"
	import FreeCard from "../../../uni_modules/free-card/free-card.vue"
	import JobScroll from "../../../uni_modules/jobscroll/jobscroll.vue"
	import CourseCard from "../../../uni_modules/course_card/course_card.vue"
	export default {
		data() {
			return {
				topBanner: [],
				index_banner: {},
				footBanner:{}
			}
		},
		onLoad() {

		},
		methods: {

		},
		mounted() {
			uni.request({
				url: "http://html5.bjsxt.cn/api/index/banner",
				//注意：写成箭头函数
				success: (res) => {
					this.topBanner = res.data.top_banner
					this.index_banner = res.data.index_banner
					this.footBanner = res.data.foot_banner
				}
			})
			
		},
		components: {
			Navbar,
			CourseNav,
			FreeCard,
			JobScroll,
			CourseCard
		}
	}
</script>

<style lang="scss">
	.home {
		display: flex;
		flex-direction: column;
		flex: 1;
		overflow: hidden;

		.index_banner_box {
			display: flex;
			width: 100%;
			padding: 10px;
			justify-content: center; //水平居中
			align-items: center; //垂直居中
			border-radius: 5px;
			overflow: hidden;

			.swiper {
				width: 100%;
				height: 260rpx;

				.banner {
					width: 700rpx;
					height: 260rpx;
				}
			}
		}

		.online_box {
			display: flex;
			width: 100%;
			justify-content: center; //垂直居中
			align-items: center; //水平居中
			box-sizing: border-box;
			overflow: hidden;
			margin-bottom: 15px;

			.online_img {
				width: 100%;
				height: 132rpx;
			}
		}
		.public_two_box{
			display: flex;
			width: 100%;
			justify-content: center; //垂直居中
			align-items: center; //水平居中
			box-sizing: border-box;
			overflow: hidden;
			padding: 0 15px;
			justify-content: space-between;//字间距增大
			align-content: space-between;//横向空间增大
			flex-wrap: wrap;//竖向空间增大
			.public_T{
				font-size: 20px;
				font-weight: 700;
			}
			
		}
		.public_title{
			width: 100%;
			display: flex;
			padding: 0 15px;
			flex-direction: column;
			
			.public_class_T{
				font-size: 22px;
				font-weight: 700;
				margin-bottom: 15px;
				
			}
		}
		.recommend_T_box{
			margin-bottom: 25px;
			
			.public_T{
				font-size: 22px;
				font-weight: 700;
				margin-bottom: 15px;
			}
		}
		.daotu_box{
			display: flex;
			box-sizing: border-box;
			flex-direction: column;
			justify-content: center;
			align-items: center;
			.daotu_T{
				font-size: 18px;
				font-weight: 700;
				margin: 15px;
			}
			.image{
				width: 699rpx;
				height: 634rpx;
				margin: 0 0 15px 0;
			}
		}
	}
</style>