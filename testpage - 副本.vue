<template>
	<view class="testpage">
		<!-- th -->
		<scroll-view 
			scroll-x="true" 
			:scroll-left="scrolleft"
			show-scrollbar="true" 
			class="vhm1"
			@scrolltoupper="upper" 
			@scrolltolower="lower" 
			@scroll="scrollth">
			<view class="vmdisflex">
				<view 
					class="vmflexv" 
					v-for="i in bdata" 
					:key="i">
					{{i}}
				</view>
			</view>
		</scroll-view>
		<!-- td内容 -->
		<view style="display: flex;">
			<view style="width: 160px;">
				<view class="vb">
					<scroll-view
						scroll-y="true"
						:scroll-top="scrollTop"
						show-scrollbar="true" 
						class="scroll-Y" 
						@scrolltoupper="upper" 
						@scrolltolower="lower" 
						@scroll="scrolltdl">
						<view class="vbdisflex">
							<view 
								class="vbflexv" 
								v-for="i in 15" 
								:key="i">
								item {{i + math}}
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
						@scrolltoupper="upper" 
						@scrolltolower="lower" 
						@scroll="scrolltdr">
						<view class="disflex">
							<view 
								class="flexv" 
								v-for="(item,i) in sdata" 
								:key="i">
								item {{item.text + math}}
							</view>
						</view>
					</scroll-view>
				</view>
			</view>
		</view>
		<!-- <view class="wh" :style="'width:' +sysw +'px'">
			<scroll-view 
				scroll-x="true" 
				scroll-y="true"
				:scroll-left="scrolleft"
				:scroll-top="scrollTop"
				show-scrollbar="true" 
				class="scroll-Y" 
				@scrolltoupper="upper" 
				@scrolltolower="lower" 
				@scroll="scroll">
				<view class="disflex">
					<view 
						class="flexv" 
						v-for="(item,i) in sdata" 
						:key="i">
						item {{item.text + math}}
					</view>
				</view>
			</scroll-view>
		</view>
		<view class="vb">
			<scroll-view
				scroll-y="true"
				:scroll-top="scrollTop"
				show-scrollbar="true" 
				class="scroll-Y" 
				@scrolltoupper="upper" 
				@scrolltolower="lower" 
				@scroll="scroll">
				<view class="vbdisflex">
					<view 
						class="vbflexv" 
						v-for="i in 10" 
						:key="i">
						item {{i + math}}
					</view>
				</view>
			</scroll-view>
		</view> -->
	</view>
</template>

<script>
	export default {
	    data() {
	        return {
	            scrollTop: 0,
				scrolleft:0,
				sysw:200,
				sdata:[],
				bdata:['标题0','标题1','标题2','标题3','标题4'],
	            old: {
	                scrollTop: 0
	            },
				math:Math.floor(Math.random()*(90-10+1)+0)
	        }
	    },
		onLoad() {
			let a={text:0,top:0};
			for(let i=0;i<60;i++){
				a={text:0,top:0}
				if(i%5==0){
					a.text = i
				}else{
					a.text = i
				}
				this.sdata.push(a);
			}
			this.sysw = uni.getSystemInfoSync().screenWidth - 160
		},
	    methods: {
	        upper: function(e) {
	            console.log(e)
	        },
	        lower: function(e) {
	            console.log(e)
	        },
	        scrollth: function(e) {
				console.log(e,e.detail.scrollTop,e.detail.scrollLeft)
	            // this.old.scrollTop = e.detail.scrollTop
				// let top = e.detail.scrollTop;
				// let left = e.detail.scrollLeft;
				this.scrolleft = e.detail.scrollLeft
	        },
			scrolltdl: function(e) {
				console.log(e,e.detail.scrollTop,e.detail.scrollLeft)
			    // this.old.scrollTop = e.detail.scrollTop
				// let top = e.detail.scrollTop;
				// let left = e.detail.scrollLeft;
				this.scrollTop = e.detail.scrollTop
			},
			scrolltdr: function(e) {
				console.log(e,e.detail.scrollTop,e.detail.scrollLeft)
			    // this.old.scrollTop = e.detail.scrollTop
				// let top = e.detail.scrollTop;
				// let left = e.detail.scrollLeft;
				this.scrolleft = e.detail.scrollLeft
				this.scrollTop = e.detail.scrollTop
			},
	        goTop: function(e) {
	            this.scrollTop = this.old.scrollTop
	            this.$nextTick(function() {
	                this.scrollTop = 0
	            });
	            uni.showToast({
	                icon:"none",
	                title:"纵向滚动 scrollTop 值已被修改为 0"
	            })
	        }
	    }
	}
</script>

<style lang="scss">
	.testpage{
		.vh{
			background: #FFFFFF;
			border-bottom: 1px solid #000000;
			box-sizing: border-box;
			width: 800px;
			overflow: auto;
			display: flex;
			.vh1{
				width: 160px;
				height: 30px;
			}
			.vh2{
				flex: 1;
				background: #FFFFFF;
			}
		}
		.vhm1{
			white-space: nowrap;
			width: 100%;
		}
		.vmdisflex{
			display: flex;
			width: 800px;
			border-bottom: 1px solid #000000;
			box-sizing: border-box;
			padding-left: 160px;
		}
		.vmflexv{
			width: 160px;
			box-sizing: border-box;
			border-right: 1px solid #000000;
			border-bottom: 1px solid #000000;
			height: 30px;
			background: #FFFFFF;
			&:first-child{
				position: fixed;
				left: 0;
			}
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
