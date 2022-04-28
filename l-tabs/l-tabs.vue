<template>
	<view class="l-tabs">
		<view class="l-tab-item" :class="{'l-tab-selected': index == lCurrent}" v-for="(item, index) in tabs" 
		@tap.stop.prevent="change(index)">
			<text class="l-tab-label">{{item.label}}</text>
			<view class="l-tab-bottom-line" v-if="index == lCurrent"></view>
		</view>
	</view>
</template>

<script>
	export default {
		props: {
			// tab
			tabs: {
				type: Array,
				default() {
					return [];
				}
			},
			// 当前选中tab
			current: {
				type: Number,
				default: 2
			}
		},
		data() {
			return {
				lCurrent: this.current,
			};
		},
		watch: {
			// 监听父组件 current 变化，以改变子组件 lCurrent
			current() {
				this.lCurrent = this.current;
			}
		},
		methods: {
			change(i){
				this.lCurrent = i;
				this.$emit("tapChange", i);
			}
		}
	}
</script>

<style scoped>
.l-tabs{
	width: 100%;
	background-color: #ffffff;
	display: flex;
}
.l-tab-item{
	display: inline-block;
	width: 100%;
	margin-top: 5px;
	position: relative;
}
.l-tab-label{
	display: block;
	font-size: 14px;
	text-align: center;
	padding: 5px 0 8px;
}
.l-tab-selected{
	color: #237ddc;
}
.l-tab-bottom-line{
	position: absolute;
	bottom: 0;
	left: 0;
	right: 0;
	margin: auto;
	width: 70%;
	height: 2px;
	background-color: #237ddc;
	animation: fadeIn .5s ease;
}
@keyframes fadeIn{
	from {
		width: 0;
	}
	to {
		width: 70%;
	}
}
</style>