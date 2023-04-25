<template>
	<view>
		<view class="free_card_box" v-for="(item,index) in teaList" :key="index">
			<view class="free_card_img">
				<image :src="item.teacher_logo" mode=""></image>
			</view>
			<view class="free_card_text">
				<view class="free_card_T">
					{{ item.limitName }}
				</view>
				<view class="free_card_info">
					<view class="free_card_info_text">
						<view class="info_text1">
							{{item.teacher_name}}
							{{item.teacher_job}}
						</view>
						<view class="">
							{{item.limitNum}}人学过
						</view>
					</view>
					<view class="free_card_info_btn" v-if="item.baoming == '立即学习'">
						{{item.baoming}}
					</view>
					<view class="free_card_info_btn free_card_info_btn1" v-else>
						{{item.baoming}}
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default{
		name:"free-card",
		data(){
			return{
				teaList:[]
			};
		},
		mounted() {
			uni.request({
				url:"http://html5.bjsxt.cn/api/index/specific?userid=2162",
				success: (res) => {
					console.log(res.data)
					this.teaList = res.data.data
				}
			})
		}
	}
</script>
	
<style lang="scss">
	.free_card_box{
		display: flex;
		padding: 10px 0;
		margin:10px;
		border-radius: 10px;
		box-shadow: 0 0 5px 1px rgba($color:#000000, $alpha: 0.1);
		box-sizing: border-box;
		align-items: center;
		margin-bottom: 15px;
		background-color: #fff;
		
		.free_card_img{
			flex-shrink: 0;//指定收缩规则，默认是1,0表示固定元素不被挤压
			width: 91rpx;
			height: 91rpx;
			border-radius: 100%;
			margin: 0 15px;
			image{
				width: 100%;
				height: 100%;
				border-radius: 100%;
			}
		}
		.free_card_text{
			width: 100%;
			display: flex;
			box-sizing: border-box;
			flex-direction: column;
			padding: 0 15px 0 0;
			
			.free_card_T{
				font-size: 16px;
				white-space: nowrap;//nowrap:文本不会换行，文本会在在同一行上继续，直到遇到 <br> 标签为止。
				text-overflow: ellipsis;//text-overflow 属性规定当文本溢出包含元素时发生的事情。ellipsis	显示省略符号来代表被修剪的文本。
				overflow: hidden;
				margin: 10px 0;
			}
			.free_card_info{
				width: 100%;
				display: flex;
				box-sizing: border-box;
				flex-flow: row nowrap;
				//flex-flow属性是弹性方向和弹性换行属性的简写。它仅适用于弹性项，因此如果容器的项不是弹性项，则 flex-flow 属性不会影响相应的项。
				//flex-flow 属性的默认值是行 nowrap，它是 flex-direction（即行）和 flex-wrap（即 nowrap）属性的默认值的串联。
				//row	flex-direction默认值。作为一行，水平地显示弹性项目。
				//nowrap  flex-wrap默认值。规定弹性项目不会换行
				justify-content: space-between;
				.free_card_info_text{
					width: 60%;
					overflow: hidden;
					font-size: 16px;
					color: #666;
					.info_text1{
						height: 20px;
						font-size: 14px;
						overflow: hidden;
					}
				}
				.free_card_info_btn{
					width: 100px;
					height: 34px;
					text-align: center;
					line-height: 34px;
					border-radius: 34px;
					background-color: #00b783;
					color: white;
					font-size: 16px;
					margin-top: 10px;
				}
				.free_card_info_btn1{
					background-color: #ddd;
				}
			}
		}
	}
</style>