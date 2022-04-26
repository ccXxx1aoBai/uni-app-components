<template>
	<view class="l-mask" @click.self="hide">
		<view class="l-popup" :style="{borderRadius: `${radius}px ${radius}px 0px 0px`, height: `${height}px`}">
			<view class="l-popup-title">
				<text class="l-popup-title-label">标题</text>
			</view>
			<view class="l-popup-content">
				{{content}}
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		props: {
			// 圆角
			radius: {
				type: Number,
				default: 25
			},
			// 弹出框高度
			height: {
				type: Number,
				default: 150
			},
			// 显示内容
			content: {
				type: String,
				default: "内容"
			}
		},
		data() {
			return {
				
			};
		},
		methods: {
			show(){
				var mask = document.querySelector(".l-mask");
				var popup = document.querySelector(".l-popup");
				mask.style.display = "block";
				mask.style.animation = "in .1s forwards";
				document.styleSheets[0].insertRule("@keyframes in{from{opacity:0}to{opacity:1}}")
				document.styleSheets[0].insertRule("@keyframes fadeIn{from{bottom:"+ (-popup.clientHeight) +"px}to{bottom:0}}")
				popup.style.animation = "fadeIn .3s forwards";
			},
			hide(){
				var mask = document.querySelector(".l-mask");
				var popup = document.querySelector(".l-popup");
				document.styleSheets[0].insertRule("@keyframes out{to{opacity:0}from{opacity:1}}")
				document.styleSheets[0].insertRule("@keyframes fadeOut{to{bottom:"+ (-popup.clientHeight) +"px}from{bottom:0}}")
				mask.style.animation = "out .1s forwards";
				popup.style.animation = "fadeOut .1s forwards";
				setTimeout(() => {
					mask.style.display = "none";
				}, 100);
			}
		},
		mounted() {
			
		}
	}
</script>

<style>
.l-mask{
	position: absolute;
	width: 100%;
	height: 100%;
	top: 0;
	background-color: rgba(0, 0, 0, .5);
	display: none;
}
.l-popup{
	width: 100%;
	background-color: #ffffff;
	position: absolute;
	bottom: 0px;
}
.l-popup-title{
	width: 100%;
	height: 40px;
}
.l-popup-title-label{
	display: block;
	color: #313131;
	text-align: center;
	line-height: 40px;
	font-size: 18px;
}
.l-popup-content{
	width: 80%;
	margin: auto;
}
</style>