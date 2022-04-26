<template>
	<view class="l-action-sheet" @touchmove.stop v-show="open" @click.self="hide">
		<view class="l-box" :animation="animationData" @click.stop>
			<view class="l-action-sheet-title">地址选择</view>
			<scroll-view scroll-y="true" class="scroll" :style="{borderRadius: `${mode == 'ios' ? '10px 10px 0 0' : '0'}`}"
			v-if="address.length > 0 ? true : false">
				<view class="l-action-sheet-box">
					<view class="l-address-list" v-for="(item, index) in address">
						<view class="l-item" @click="check(index)">
							<view class="l-radio">
								<text class="l-radio-outer" :class="{'l-radio-checked': index == current}"></text>
								<text class="l-radio-inner"></text>
							</view>
							<view class="l-info">
								<text class="l-address-desc">{{item.desc}}</text>
								<view class="l-userinfo">
									<text class="l-user-name">{{item.name}}</text>
									<text class="l-user-tel">{{item.tel}}</text>
								</view>
							</view>
						</view>
					</view>
				</view>
			</scroll-view>
			<view class="l-address-add" v-else @click="addAddress">
				添加地址
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		props: {
			// 地址列表数据
			address: {
				type: Array,
				default() {
					return [];
				}
			},
			// 弹出框border-radius
			mode: {
				type: String,
				default: 'md'
			}
		},
		data() {
			return {
				current: 0,
				open: true,
				animationData: {}
			};
		},
		methods: {
			addAddress(){
				
			},
			check(i){
				this.current = i;
				this.open = false;
				this.$emit("updateLocation", this.address[i].desc);
			},
			show(){
				this.open = true;
			},
			hide(){
				this.open = false;
			}
		}
	}
</script>

<style scoped>
.l-action-sheet{
	position: absolute;
	width: 100%;
	height: 100%;
	top: 0;
	left: 0;
	background-color: rgba(0, 0, 0, .8);
	z-index: 99;
	overflow: hidden;
}
.l-box{
	position: absolute;
	width: 100%;
	height: 50%;
	bottom: 0;
	background-color: #eaeaea;
}
.l-action-sheet-title{
	width: 100%;
	height: 30px;
	line-height: 30px;
	background-color: #ffffff;
	padding: 0 10px;
}
.scroll{
	width: 100%;
	height: calc(100% - 35px);
	margin: 5px 0;
}
.l-address-list{
	width: 100%;
	height: auto;
}
.l-item{
	width: 96%;
	margin: 0px auto 10px;
	background-color: #ffffff;
	border-radius: 5px;
	padding: 5px 0;
}
.l-radio{
	display: inline-block;
	width: 16px;
	height: 16px;
	position: relative;
	margin: 10px;
}
.l-radio .l-radio-outer{
	position: absolute;
	display: block;
	width: 20px;
	height: 20px;
	border: 1px solid #e5e5e5;
	border-radius: 50%;
	background-color: #ffffff;
	box-sizing: border-box;
}
.l-radio .l-radio-checked{
	background-color: #ffbb1b;
}
.l-radio .l-radio-inner{
	position: absolute;
	top: 7px;
	left: 7px;
	width: 6px;
	height: 6px;
	background-color: #ffffff;
	border-radius: 50%;
}
.l-info{
	display: inline-block;
}
.l-address-desc{
	font-size: 14px;
	display: block;
	padding: 2px 10px;
}
.l-userinfo{
	padding: 2px 10px;
}
.l-userinfo text{
	font-size: 12px;
	color: #666666;
}
.l-user-tel{
	padding: 0 10px;
}
.l-address-add{
	width: 90%;
	height: 40px;
	margin: 15px auto;
	color: #333333;
	font-size: 14px;
	line-height: 40px;
	text-align: center;
	border-radius: 5px;
	background-color: #ffffff;
}
</style>