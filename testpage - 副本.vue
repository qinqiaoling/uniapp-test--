<template>
	<view class="testpage">
		<!-- th -->
		<view style="display: flex;">
			<view style="width: 160px;overflow: hidden;">
				<scroll-view
					class="vhm1"
					scroll-with-animation>
					<view class="vmdisflex">
						<view 
							class="vmflexv" 
							v-for="i in 1" 
							:key="i">
							标题 {{i}}
						</view>
					</view>
				</scroll-view>
			</view>
			<view :style="'width:' +sysw +'px'">
				<scroll-view
					scroll-x="true" 
					:scroll-left="scrolleft"
					show-scrollbar="true" 
					class="vhm1"
					scroll-with-animation
					@scroll="scrollth">
					<view class="vmdisflex">
						<view 
							class="vmflexv" 
							v-for="i in 4" 
							:key="i">
							标题 {{i+1}}
						</view>
					</view>
				</scroll-view>
			</view>
		</view>
		<!-- td内容 -->
		<view style="display: flex;">
			<view style="width: 160px;">
				<view class="vb">
					<scroll-view
						scroll-y="true"
						:scroll-top="scrollTop"
						show-scrollbar="true" 
						class="scroll-Y" 
						scroll-with-animation
						@scroll="scrolltdl">
						<view class="vbdisflex">
							<view 
								class="vbflexv" 
								v-for="i in 15" 
								:key="i">
								item {{i}}
							</view>
						</view>
					</scroll-view>
				</view>
			</view>
			<view :style="'width:' +sysw +'px'">
				<view class="wh" :style="'width:' +sysw +'px'">
					<scroll-view 
						scroll-x="true" 
						scroll-y="true"
						:scroll-left="scrolleft"
						:scroll-top="scrollTop"
						show-scrollbar="true" 
						class="scroll-Y" 
						scroll-with-animation
						@scroll="scrolltdr">
						<view class="disflex">
							<view 
								class="flexv" 
								v-for="i in 60" 
								:key="i">
								item-{{i}}
							</view>
						</view>
					</scroll-view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
	    data() {
	        return {
	            scrollTop: 0,
				scrolleft:0,
				sysw:200,
	        }
	    },
		onLoad() {
			this.sysw = uni.getSystemInfoSync().screenWidth - 160
		},
	    methods: {
	        scrollth: function(e) {
				console.log(e,'距离顶部距离',e.detail.scrollTop,'距离左边距离',e.detail.scrollLeft)
				this.scrolleft = e.detail.scrollLeft
	        },
			scrolltdl: function(e) {
				console.log(e,'距离顶部距离',e.detail.scrollTop,'距离左边距离',e.detail.scrollLeft)
				this.scrollTop = e.detail.scrollTop
			},
			scrolltdr: function(e) {
				console.log(e,'距离顶部距离',e.detail.scrollTop,'距离左边距离',e.detail.scrollLeft)
				this.scrolleft = e.detail.scrollLeft
				this.scrollTop = e.detail.scrollTop
			},
	    }
	}
</script>

<style lang="scss">
	.testpage{
		.vhm1{
			white-space: nowrap;
			width: 100%;
		}
		.vmdisflex{
			display: flex;
			// width: 800px;
			width: 640px;
			border-bottom: 1px solid #000000;
			box-sizing: border-box;
			// padding-left: 160px;
		}
		.vmflexv{
			width: 160px;
			box-sizing: border-box;
			border-right: 1px solid #000000;
			border-bottom: 1px solid #000000;
			height: 30px;
			background: #FFFFFF;
			// &:first-child{
			// 	position: fixed;
			// 	left: 0;
			// }
		}
		.wh{
			float: right;
		}
		.vb{
			width: 160px;
			float: left;
			.vbdisflex{
				display: flex;
				flex-wrap: wrap;
				width: 100%;
				position: relative;
				.vbflexv{
					width: 160px;
					box-sizing: border-box;
					border: 1px solid #000000;
					height: 30px;
				}
			}
		}
		.scroll-Y {
			height: 200px;
		}
		.scroll-view_H {
			white-space: nowrap;
			width: 100%;
		}
		.disflex{
			display: flex;
			flex-wrap: wrap;
			width: 640px;
			position: relative;
			.flexv{
				width: 160px;
				box-sizing: border-box;
				border: 1px solid #000000;
				height: 30px;
			}
		}
	}
</style>
