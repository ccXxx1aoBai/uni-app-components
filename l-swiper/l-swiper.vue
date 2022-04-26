<template>
	<view class="l-swiper" :style="{
		borderRadius: `${radius}px`
	}">
		<swiper :indicator-dots="false" :current="current" :autoplay="autoplay" :circular="circular" :interval="interval" 
		:duration="duration" @change="change" :style="{height: `${height}px`,borderRadius: `${radius}px`}">
			<swiper-item @tap.stop.prevent="clickList(index)" v-for="(item, index) in list"
			class="l-swiper-item">
				<image class="l-swiper-image" :src="item[name]" :style="{borderRadius: `${radius}px`}"></image>
				<view class="l-swiper-title" v-if="item.title && showTitle">
					{{item.title}}
				</view>
			</swiper-item>
		</swiper>
		<view class="l-swiper-indicator" v-if="!showTitle && indicator">
			<block v-if="mode == 'rect'">
				<view class="l-swiper-indicator-rect" :style="{left:`${left}`}" v-for="(item, index) in list" 
				:class="{'l-swiper-indicator-rect-active': index == lCurrent}"></view>
			</block>
			<block v-if="mode == 'dot'">
				<view class="l-swiper-indicator-dot" :style="{left:`${left}`}" v-for="(item, index) in list"
				:class="{'l-swiper-indicator-dot-active': index == lCurrent}"></view>
			</block>
			<block v-if="mode == 'round'">
				<view class="l-swiper-indicator-round" :style="{left:`${left}`}" v-for="(item, index) in list"
				:class="{'l-swiper-indicator-round-active': index == lCurrent}"></view>
			</block>
			<block v-if="mode == 'number'">
				<view class="l-swiper-indicator-number" :style="{left:`${left}`}">{{ lCurrent + 1 }}/{{ list.length }}</view>
			</block>
		</view>
	</view>
</template>

<script>
	export default {
		props: {
			// 轮播图数据 [{'url': '地址', 'title': '标题'}] title显示需结合showTitle使用 url 可使用别名 需使用name指定
			list: {
				type: Array,
				default (){
					return []
				},
			},
			// 显示标题
			showTitle: {
				type: Boolean,
				default: false
			},
			// 数据中图片属性名
			name: {
				type: String,
				default: 'url',
			},
			// 是否显示指示点
			indicator: {
				type: Boolean,
				default: false
			},
			// 是否自动播放
			autoplay: {
				type: Boolean,
				default: true
			},
			// 是否衔接滑动 即到最后一张时接着滑动 是否自动切换到第一张
			circular: {
				type: Boolean,
				default: false
			},
			// 自动播放间隔
			interval: {
				type: Number,
				default: 3000
			},
			// 起始页面
			current: {
				type: Number,
				default: 0
			},
			// 动画时长（毫秒）
			duration: {
				type: Number,
				default: 300
			},
			// 圆角
			radius: {
				type: Number,
				default: 8
			},
			// 轮播图高度
			height: {
				type: Number,
				default: 150
			},
			// 指示点样式
			mode: {
				type: String,
				default: "dot"
			},
			// 指示点距离左侧距离
			left: {
				type: String,
				default: "0px"
			}
		},	
		data() {
			return {
				lCurrent: this.current,
			}
		},
		methods: {
			clickList(index){
				console.log(index);
				this.$emit("click", index)
			},
			change(event){
				this.lCurrent = event.detail.current;
			},
		}
	}
</script>

<style>
.l-swiper{
	width: 100%;
	position: relative;
	overflow: hidden;
}
.l-swiper-image{
	width: 100%;
	height: 100%;
	pointer-events: none;
}
.l-swiper-title{
	width: 100%;
	padding: 5px;
	position: absolute;
	bottom: 0;
	z-index: 99;
	color: #000000;
	text-indent: 12px;
	font-size: 12px;
	color: #ffffff;
	background-color: rgba(0, 0, 0, 0.3);
	overflow: hidden;
	text-overflow: ellipsis;
	white-space: nowrap;
}
.l-swiper-indicator{
	position: absolute;
	width: 100%;
	padding: 0 24rpx;
	display: flex;
	bottom: 10px;
	z-index: 99;
}
.l-swiper-indicator-rect {
	width: 26rpx;
	height: 8rpx;
	margin: 0 6rpx;
	transition: all 0.5s;
	background-color: rgba(0, 0, 0, 0.3);
	position: relative;
	top: 0px;
}
.l-swiper-indicator-rect-active {
	background-color: rgba(255, 255, 255, 0.8);
}
.l-swiper-indicator-dot {
	position: absolute;
	right: 14rpx;
	width: 14rpx;
	height: 14rpx;
	margin: 0 6rpx;
	border-radius: 20rpx;
	transition: all 0.5s;
	background-color: rgba(0, 0, 0, 0.3);
	position: relative;
	top: 0px;
}
.l-swiper-indicator-dot-active {
	background-color: rgba(255, 255, 255, 0.8);
}
.l-swiper-indicator-round {
	width: 14rpx;
	height: 14rpx;
	margin: 0 6rpx;
	border-radius: 20rpx;
	transition: all 0.5s;
	background-color: rgba(0, 0, 0, 0.3);
	position: relative;
	top: 0px;
}
.l-swiper-indicator-round-active {
	width: 34rpx;
	background-color: rgba(255, 255, 255, 0.8);
}
.l-swiper-indicator-number {
	padding: 6rpx 16rpx;
	line-height: 1;
	background-color: rgba(0, 0, 0, 0.3);
	border-radius: 100rpx;
	font-size: 26rpx;
	color: rgba(255, 255, 255, 0.8);
	position: relative;
	top: 0px;
}
</style>
