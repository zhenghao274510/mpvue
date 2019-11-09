<template>
<!-- 	<view>
		<page-head title="scroll-view,区域滚动视图"></page-head>
		<view class="uni-padding-wrap uni-common-mt">
			<view class="uni-title uni-common-mt">
				Vertical Scroll
				<text>\n纵向滚动</text>
			</view>
			<view>
				<scroll-view :scroll-top="scrollTop" scroll-y="true" class="scroll-Y" @scrolltoupper="upper" @scrolltolower="lower"
				@scroll="scroll">
					<view id="demo1" class="scroll-view-item uni-bg-red">A</view>
					<view id="demo2" class="scroll-view-item uni-bg-green">B</view>
					<view id="demo3" class="scroll-view-item uni-bg-blue">C</view>
				</scroll-view>
			</view>
			<view @tap="goTop" class="uni-link uni-center uni-common-mt">
				点击这里返回顶部
			</view>
			
			<view class="uni-title uni-common-mt">
				Horizontal Scroll
				<text>\n横向滚动</text>
			</view>
			<view>
				<scroll-view class="scroll-view_H" scroll-x="true" @scroll="scroll" scroll-left="120">
					<view id="demo1" class="scroll-view-item_H uni-bg-red">A</view>
					<view id="demo2" class="scroll-view-item_H uni-bg-green">B</view>
					<view id="demo3" class="scroll-view-item_H uni-bg-blue">C</view>
				</scroll-view>
			</view>
		</view>
		</view> -->
		<view class="cont">
			<view class="nomore">
				
			</view>
			<view class="test_list">
				<view class="img_list">
					<image src="/static/img/cate3.jpg" mode="scaleToFill"></image>
				</view>
					<view class="img_list">
					<image src="/static/img/cate4.jpg" mode="scaleToFill"></image>
				</view>
					<view class="img_list">
					<image src="/static/img/cate5.jpg" mode="scaleToFill"></image>
				</view>
					<view class="img_list">
					<image src="/static/img/cate6.jpg" mode="scaleToFill"></image>
				</view>
				
			</view>
		</view>
</template>
<script>
	export default {
		data() {
			return {
				scrollTop: 0,
				old: {
					scrollTop: 0
				}
			}
		},
		onLoad() {
			this.$nextTick(()=>{
				this.load();
			})
			
		},
		onPageScroll() {
			
		},
		methods: {
			load(){
					uni.createSelectorQuery().selectAll('.img_list').boundingClientRect((images) => {
						console.log(images)
					images.forEach((image, index) => {
						
						// if (image.top <= this.windowHeight) {
							// this.list[image.dataset.index].show = true;
						// }
					})
				}).exec()
			},
			upper: function(e) {
				console.log(e)
			},
			lower: function(e) {
				console.log(e)
			},
			scroll: function(e) {
				console.log(e)
				this.old.scrollTop = e.detail.scrollTop
			},
			goTop: function(e) {
				// 解决view层不同步的问题
				this.scrollTop = this.old.scrollTop
				this.$nextTick(function() {
					this.scrollTop = 0
				});
				uni.showToast({
					icon:"none",
					title:"纵向滚动 scrollTop 值已被修改为 0"
				})
			}
		}
	}
</script>

<style>
	.nomore{
		height: 500upx;
	}
	.test_list{
		width: 100%;
		display: flex;
		flex-direction: row;
		flex-wrap: wrap;
	}
	.img_list{
		width:50%;
		padding: 10upx;
	}
	.img_list image{
		width: 100%;
	}
	
	
	.scroll-Y {
		height: 300upx;
	}

	.scroll-view_H {
		white-space: nowrap;
		width: 100%;
	}

	.scroll-view-item {
		height: 300upx;
		line-height: 300upx;
		text-align: center;
		font-size: 36upx;
	}

	.scroll-view-item_H {
		display: inline-block;
		width: 100%;
		height: 300upx;
		line-height: 300upx;
		text-align: center;
		font-size: 36upx;
	}
</style>