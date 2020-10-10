<template>
	<view class="uni-tabbar-box">
		<view class="uni-tabbar" :style="{ backgroundColor: backgroundColor }">
			<view class="uni-tabbar-border" :style="{ backgroundColor: borderColor }"></view>
			<slot></slot>
		</view>
	</view>
</template>

<script>

export default {
	data() {
		return {

		};
	},
	props: {
		backgroundColor: {
			type: String,
			default: '#eee'
		},
		borderColor: {
			type: String,
			default: '#aaa'
		}
	}
};
</script>

<style>
.uni-tabbar-box {
	display: block;
}
.uni-tabbar-box,
.uni-tabbar-box .uni-tabbar {
	box-sizing: border-box;
	position: fixed;
	left: 0;
	bottom: 0;
	width: 100%;
	z-index: 998;
}
.uni-tabbar-box .uni-tabbar {
	display: flex;
	justify-content: space-around;
	padding-bottom: 0;
	padding-bottom: constant(safe-area-inset-bottom);
	padding-bottom: env(safe-area-inset-bottom);
}
.uni-tabbar-box .uni-tabbar ~ .uni-placeholder {
	width: 100%;
	height: 50px;
	margin-bottom: 0;
	margin-bottom: constant(safe-area-inset-bottom);
	margin-bottom: env(safe-area-inset-bottom);
}
.uni-tabbar-box .uni-tabbar * {
	box-sizing: border-box;
}

.uni-tabbar-box .uni-tabbar-border {
	position: absolute;
	left: 0;
	top: 0;
	width: 100%;
	height: 1px;
	/* -webkit-transform: scaleY(0.5); */
	transform: scaleY(0.5);
}

</style>
