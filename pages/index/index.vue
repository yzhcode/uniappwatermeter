<template>
	<view class="index_content">
		<view class="page_content">
			<index1 v-if="show_index == 1" ref="index1"></index1>
			<index2 v-else-if="show_index == 2" ref="index2"></index2>
			<index3 v-else-if="show_index == 3" ref="index3"></index3>
			<index4 v-else-if="show_index == 4" ref="index4"></index4>
			<index5 v-else-if="show_index == 5" ref="index5"></index5>
		</view>

		<view class="tabBar">
			<!-- 导航的中间圆圈 -->
			<view class="border_box"><view class="tabBar_miden_border"></view></view>
			<view class="tabBar_list">
				<view v-for="item in tab_nav_list" :key="item.id" :class="{ tabBar_item: item.id != 3, tabBar_item2: item.id == 3 }" @tap="cut_index(item.id)">
					<image v-if="show_index == item.id" :src="`../../static/tabBar/${item.id}${item.id}.png`"></image>
					<image v-else :src="`../../static/tabBar/${item.id}.png`"></image>
					<view :class="{ tabBar_name: true, nav_active: show_index == item.id }">{{ item.name }}</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
import index1 from './pages/index1.vue';
import index2 from './pages/index2.vue';
import index3 from './pages/index3.vue';
import index4 from './pages/index4.vue';
import index5 from './pages/index5.vue';

export default {
	components: {
		index1,
		index2,
		index3,
		index4,
		index5
	},
	data() {
		return {
			show_index: 1,
			tab_nav_list: [{ id: 1, name: '首页' }, { id: 2, name: '分类' }, { id: 3, name: '推荐' }, { id: 4, name: '购物车' }, { id: 5, name: '我' }]
		};
	},
	methods: {
		cut_index(type) {
			console.log('显示：', type);
			let self = this;
			self.show_index = type;
		}
	}
};
</script>

<style lang="scss">
$tabbarheight: 100rpx;
$tabbarbgcolor: rgba($color: #f5f, $alpha: 1.0);
.index_content {
	border: 2px solid #f00;
	.page_content {
		border: 2px solid #0f0;
		// 这里本来是想用calc(env(safe-area-inset-bottom)+$tabbarheight)
		// 但是没生效，暂时没搞懂时怎么回事，只有先分成2部分撑开底部
		margin-bottom: $tabbarheight;
		padding-bottom: constant(safe-area-inset-bottom); /* 兼容 iOS < 11.2 */
		padding-bottom: env(safe-area-inset-bottom); /* 兼容 iOS >= 11.2 */
	}
	.tabBar {
		width: 100%;
		height: $tabbarheight;
		background: $tabbarbgcolor;
		border-top: 1px solid #e5e5e5;
		padding-bottom: constant(safe-area-inset-bottom); /* 兼容 iOS < 11.2 */
		padding-bottom: env(safe-area-inset-bottom); /* 兼容 iOS >= 11.2 */
		position: fixed;
		bottom: 0px;
		left: 0px;
		right: 0px;
		display: flex;
		align-items: center;
		justify-content: center;
		.tabBar_list {
			width: 86%;
			display: flex;
			justify-content: space-between;
			image {
				width: 48rpx;
				height: 48rpx;
				margin-bottom: 2rpx;
			}
			.tabBar_item {
				width: 68rpx;
				display: flex;
				justify-content: center;
				align-items: center;
				flex-direction: column;
				font-size: 20rpx;
				color: #969ba3;
			}
			.tabBar_item2 {
				width: 68rpx;
				height: 100%;
				display: flex;
				justify-content: center;
				align-items: center;
				flex-direction: column;
				font-size: 20rpx;
				color: #969ba3;
				margin-top: -20rpx;
				position: relative;
				z-index: 101;
				image {
					width: 68rpx;
					height: 68rpx;
				}
			}
		}
	}
	.border_box {
		// pointer-events: none; 事件穿透解决z-index层级问题
		width: 100%;
		height: $tabbarheight;
		display: flex;
		justify-content: center;
		align-items: center;
		position: fixed;
		left: 0px;
		bottom: 50rpx;
		z-index: 100;
		pointer-events: none;
		padding-bottom: constant(safe-area-inset-bottom); /* 兼容 iOS < 11.2 */
		padding-bottom: env(safe-area-inset-bottom); /* 兼容 iOS >= 11.2 */
		.tabBar_miden_border {
			width: 100rpx;
			height: 50rpx;
			border-top: 2rpx solid #e5e5e5;
			border-radius: 50rpx 50rpx 0 0; /* 左上、右上、右下、左下 */
			background: $tabbarbgcolor;
		}
	}
}
</style>
