<template>
	<view class="uni-tabbar__item" @tap="selectedItem()">
		<view class="uni-tabbar__bd">
			<view class="uni-tabbar__icon" v-if="imageSrc.length > 0"><image :src="isSelected?((selectedImageSrc.length > 0)?selectedImageSrc:imageSrc):imageSrc"></image></view>
			<view class="uni-tabbar__label" v-if="title.length > 0" :style="textStyle">{{ title }}</view>
			<view class="uni-tabbar__badge" v-if="badge.length>0"><text>{{badge}}</text></view>
			<view class="uni-tabbar__reddot" v-if="reddot"></view>
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
		isSelected: {
			type: Boolean,
			default: false
		},
		title: {
			type: String,
			default: ''
		},
		name: {
			type: String,
			default: ''
		},
		normalImageSrc: {
			type: String,
			default: ''
		},
		selectedImageSrc: {
			type: String,
			default: ''
		},
		normalTextColor: {
			type: String,
			default: '#999'
		},
		selectedTextColor: {
			type: String,
			default: '#007AFF'
		},
		textFontSize: {
			type: String,
			default: '12px'
		},
		badge: {
			type: String,
			default: ''
		},
		reddot: {
			type: Boolean,
			default: true
		}
	},
	computed: {
		textStyle() {
			return {
				color: this.isSelected?this.selectedTextColor:this.normalTextColor,
				fontSize: this.textFontSize
			}
		},
		imageSrc () {
			return (this.isSelected && (this.selectedImageSrc.length > 0))?this.selectedImageSrc:this.normalImageSrc
		}
		
	},
	methods: {
		// 切换组件
		selectedItem() {
			console.log("selectedItem");
			this.$emit("clickItem", (this.name.length > 0)?this.name:this.title);
		}
	}
};
</script>

<style scoped>

.uni-tabbar__item {
	flex-direction: column;
	flex: 1;
	font-size: 0;
	text-align: center;
	/* -webkit-tap-highlight-color: rgba(0, 0, 0, 0); */
}
.uni-tabbar__bd,
.uni-tabbar__item {
	display: flex;
	justify-content: center;
	align-items: center;
}
.uni-tabbar__bd {
	position: relative;
	height: 50px;
	flex-direction: column;
	cursor: pointer;
}
.uni-tabbar__icon {
	position: relative;
	display: inline-block;
	margin-top: 5px;
	width: 24px;
	height: 24px;
}
.uni-tabbar__icon.uni-tabbar__icon__diff {
	margin-top: 0;
	width: 34px;
	height: 34px;
}
.uni-tabbar__icon image {
	width: 100%;
	height: 100%;
}
.uni-tabbar__label {
	position: relative;
	text-align: center;
	font-size: 10px;
	line-height: 1.8;
}
.uni-tabbar-border {
	position: absolute;
	left: 0;
	top: 0;
	width: 100%;
	height: 1px;
	/* -webkit-transform: scaleY(0.5); */
	transform: scaleY(0.5);
}
.uni-tabbar__badge {
	position: absolute;
	top: 0;
	right: 0;
	min-width: 16px;
	height: 16px;
	border-radius: 16px;
	padding: 0 2px;
	background-color: #f43530;
	color: #fff;
	font-size: 13px;
	line-height: 16px;
	font-weight: bold;
	/* -webkit-transform: translate(40%, -20%); */
	transform: translate(40%, 0%);
}
.uni-tabbar__reddot {
	position: absolute;
	top: 0;
	right: 0;
	width: 10px;
	height: 10px;
	border-radius: 50%;
	background-color: #f43530;
	transform: translate(40%, 20%);
}
</style>
