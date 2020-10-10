<template>
	<view>
		<text>{{params}}</text>
	</view>
</template>

<script>
export default {
	data() {
		return {
			params: '2--'
		};
	},
	methods: {
		
	},
	mounted() {
	    var self = this;
	    setTimeout(function () {
	        self.params = self.params + 'bbb'
	    }, 3000);
	}
};
</script>

<style lang="scss"></style>
