<template>
	<view>
		<page-head :title="title"></page-head>
		<view class="uni-common-mt">
			<view>
				<map :latitude="latitude" :longitude="longitude" :markers="covers">
				</map>
			</view>
		</view>
	</view>
</template>
<script>
	export default {
		data() {
			return {
				title: 'map',
				latitude: "39.9085",
				longitude: "116.39747",
				covers: [{
					latitude: 39.9085,
					longitude: 116.39747,
					// #ifdef APP-PLUS
					iconPath: '../../../static/app-plus/location@3x.png',
					// #endif
					// #ifndef APP-PLUS
					iconPath: '../../../static/location.png',
					// #endif
				}, {
					latitude: 39.90,
					longitude: 116.39,
					// #ifdef APP-PLUS
					iconPath: '../../../static/app-plus/location@3x.png',
					// #endif
					// #ifndef APP-PLUS
					iconPath: '../../../static/location.png',
					// #endif
				}]
			}
		},
		onLoad(){
			// this.getCurrentPosition();
		},
		methods: {
			getCurrentPosition(){
				uni.authorize({
    scope: 'scope.userLocation',
    success() {
        uni.getLocation({
			type: 'jcg02',
			success: res => {
				console.log(res)
			},
			fail: () => {},
			complete: () => {}
		})
    }
})

			}
         

		}
	}
</script>
<style>
	map {
		width: 100%;
		height: 600upx;
	}
</style>
