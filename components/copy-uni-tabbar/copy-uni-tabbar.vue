<template>
	<view class="uni-tabbar-box">
		<view class="uni-tabbar" :style="{ backgroundColor: backgroundColor }">
			<view class="uni-tabbar-border" :style="{ backgroundColor: borderColor }"></view>
			<block v-for="(item, index) in tabbarList" :key="item.title">
				<view class="uni-tabbar__item" @tap="selectedItem(index)">
					<view class="uni-tabbar__bd">
						<view class="uni-tabbar__icon"><img :src="(index == selectedIndex)?item.selectedImage:item.image" /></view>
						<view class="uni-tabbar__label" :style="(index == selectedIndex)?selectedItemStyle:itemStyle">{{ item.title }}</view>
					</view>
				</view>
			</block>
		</view>
	</view>
</template>

<script>
	
export default {
	data() {
		return {
			selectedIndex: 0
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
		},
		textColor: {
			type: String,
			default: '#0f0'
		},
		selectedTextColor: {
			type: String,
			default: '#ff0'
		},
		textFontSize: {
			type: String,
			default: '12px'
		},
		tabbarList: {
			type: Array,
			default:[
				{ title: '首页a', image: '/static/tabBar/1.png', selectedImage: '/static/tabBar/11.png' },
				{ title: '首页2', image: '/static/tabBar/2.png', selectedImage: '/static/tabBar/22.png' },
				{ title: '首页3', image: '/static/tabBar/3.png', selectedImage: '/static/tabBar/33.png' },
				{ title: '首页4', image: '/static/tabBar/4.png', selectedImage: '/static/tabBar/44.png' },
				{ title: '首页5', image: '/static/tabBar/5.png', selectedImage: '/static/tabBar/55.png' }
			]
		}
	},
	computed: {
		itemStyle() {
			return {
				color: this.textColor,
				fontSize: this.textFontSize
			}
		},
		selectedItemStyle() {
			return {
				color: this.selectedTextColor,
				fontSize: this.textFontSize
			}
		}
	},
	methods: {
		// 切换组件
		selectedItem(index) {
			let self = this;
			self.selectedIndex = index;
		
			
		},
		// onPullDownRefresh() {
		// 	uni.showToast({
		// 		title: `第${this.show_index + 1}个页面的刷新`
		// 	});
		// 	setTimeout(function() {
		// 		uni.stopPullDownRefresh();
		// 	}, 2000);
		// 	console.log('下拉刷新四个组件公用的下拉刷新方法,根据在哪个页面下拉执行哪个页面的刷新方方法即可');
		// 	console.log('如果想要自定义刷新的话，插件市场就有一个   非常好用也非常容易入手');
		// }
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
	display: -webkit-box;
	display: -webkit-flex;
	display: flex;
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
.uni-tabbar-box .uni-tabbar__item {
	/* -webkit-flex-direction: column; */
	flex-direction: column;
	/* 	-webkit-box-flex: 1;
	-webkit-flex: 1; */
	flex: 1;
	font-size: 0;
	text-align: center;
	/* -webkit-tap-highlight-color: rgba(0, 0, 0, 0); */
}
.uni-tabbar-box .uni-tabbar__bd,
.uni-tabbar-box .uni-tabbar__item {
	display: -webkit-box;
	display: -webkit-flex;
	display: flex;
	/* 	-webkit-box-pack: center;
	-webkit-justify-content: center; */
	justify-content: center;
	/* 	-webkit-box-align: center;
	-webkit-align-items: center; */
	align-items: center;
	/* 	-webkit-box-orient: vertical;
	-webkit-box-direction: normal; */
}
.uni-tabbar-box .uni-tabbar__bd {
	position: relative;
	height: 50px;
	/* -webkit-flex-direction: column; */
	flex-direction: column;
	cursor: pointer;
}
.uni-tabbar-box .uni-tabbar__icon {
	position: relative;
	display: inline-block;
	margin-top: 5px;
	width: 24px;
	height: 24px;
}
.uni-tabbar-box .uni-tabbar__icon.uni-tabbar__icon__diff {
	margin-top: 0;
	width: 34px;
	height: 34px;
}
.uni-tabbar-box .uni-tabbar__icon img {
	width: 100%;
	height: 100%;
}
.uni-tabbar-box .uni-tabbar__label {
	position: relative;
	text-align: center;
	font-size: 10px;
	line-height: 1.8;
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
.uni-tabbar-box .uni-tabbar__reddot {
	position: absolute;
	top: 0;
	right: 0;
	width: 12px;
	height: 12px;
	border-radius: 50%;
	background-color: #f43530;
	color: #fff;
	/* -webkit-transform: translate(40%, -20%); */
	transform: translate(40%, -20%);
}
.uni-tabbar-box .uni-tabbar__badge {
	width: auto;
	height: 16px;
	line-height: 16px;
	border-radius: 16px;
	min-width: 16px;
	padding: 0 2px;
	font-size: 12px;
	text-align: center;
	white-space: nowrap;
}
</style>
