<template>
	<view class="index_content">
		<view class="page_content">
		<!-- 	<keep-alive>
			<component v-bind:is="currentTabComponent" :ref="currentTabComponent"></component>
			</keep-alive> -->
	
			<index1 v-show="selectedIndex == 0" ref="index1"></index1>
			<index2 v-show="selectedIndex == 1" ref="index2"></index2>
			<index3 v-show="selectedIndex == 2" ref="index3"></index3>
			<index4 v-show="selectedIndex == 3" ref="index4"></index4>
			<index5 v-show="selectedIndex == 4" ref="index5"></index5>
	
		</view>
		<custom-uni-tabbar>
			<block v-for="(item, index) in tabbarList" :key="item.title">
				<custom-uni-tabbar-item
					:isSelected="selectedIndex == index"
					:title="item.title"
					:name="item.title"
					:normalImageSrc="item.image"
					:selectedImageSrc="item.selectedImage"
					@clickItem="clickItem"
				/>
			</block>
		</custom-uni-tabbar>
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
			selectedIndex: 0,
			tabbarList: [
				{ title: '首页a', image: '/static/tabBar/1.png', selectedImage: '/static/tabBar/11.png' },
				{ title: '首页b', image: '/static/tabBar/2.png', selectedImage: '/static/tabBar/22.png' },
				{ title: '首页c', image: '/static/tabBar/3.png', selectedImage: '/static/tabBar/33.png' },
				{ title: '首页d', image: '/static/tabBar/4.png', selectedImage: '/static/tabBar/44.png' },
				{ title: '首页e', image: '/static/tabBar/5.png', selectedImage: '/static/tabBar/55.png' }
			]
		};
	},
	methods: {
		// 切换组件
		clickItem(text) {
			let self = this;
			console.log('click:', text);
			self.tabbarList.some(function(item, index, array) {
				if (item.title == text) {
					self.selectedIndex = index;
					return true;
				} else {
					return false;
				}
			});
		},
	},
	computed: {
		currentTabComponent() {
			return 'index' + (this.selectedIndex+1);
		}
	}
};
</script>

<style lang="scss"></style>
