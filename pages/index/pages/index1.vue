<template>
	<view>
		<uni-nav-bar left-icon="back" left-text="返回2" right-text="菜单" title="导航栏组件" status-bar background-color="#f0f"></uni-nav-bar>
		<text>{{params}}</text>
	</view>
</template>

<script>
	import uniNavBar from "@/components/uni-nav-bar/uni-nav-bar.vue"
	
export default {
	components: {uniNavBar},
	data() {
		return {
			params: '1--'
		};
	},
	methods: {
		
	},
	mounted() {
	    var self = this;
	    setTimeout(function () {
	        self.params = self.params + 'aaa'
	    }, 3000);
	}
};
</script>

<style lang="scss">
	uni-nav-bar {
		margin-top: 0;
		margin-top: constant(safe-area-inset-top);
		margin-top: env(safe-area-inset-top);
	}
</style>
