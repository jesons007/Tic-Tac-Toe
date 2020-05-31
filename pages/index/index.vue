<template>
 	<view>
 		<!-- <uni-section title="" type="line">
			<button type="warn"  size="mini" @click="clear()">清空</button>
			<button type="primary" style="margin-left: 10rpx;" size="mini" >添加</button>
		</uni-section> -->
		
		<view class="c-2">
			<button type="warn" plain="true" @click="start('R')">{{aaR}}</button>
		</view>
		
		
		<uni-grid :column="3" :highlight="false" class="grid-1" :showBorder="true" border-color="#03a9f4" @change="change">
			<uni-grid-item v-for="(item, index) in items" :index="index" :key="index">
				<view class="grid-item-box">
					<image :src="item.url" class="image" v-if="item.checked" mode="aspectFill" />
					
				</view>
		    </uni-grid-item>
		</uni-grid>
		
		<view class="c-3">
			<button type="primary" plain="true" @click="start('B')">{{aaB}}</button>
		</view>
		
		<view class="c-4">
			<button type="default" @click="Restart()">重新开始</button>
		</view>
	
 	</view>
 </template>
 
 <script>
	import uniGrid from "@/components/uni-grid/uni-grid.vue"
	import uniGridItem from "@/components/uni-grid-item/uni-grid-item.vue"
	
	var red_url = "/static/red.png"
	var blue_url= "/static/blue.png"
 	export default {
 		components: {
			uniGrid,
			uniGridItem
 		},
		onLoad() {
			
		},
 		data() {
 			return {
 				items: [
					{checked:false,side:'n',url:"/static/red.png"},
					{checked:false,side:'n',url:"/static/red.png"},
					{checked:false,side:'n',url:"/static/red.png"},
					{checked:false,side:'n',url:"/static/red.png"},
					{checked:false,side:'n',url:"/static/red.png"},
					{checked:false,side:'n',url:"/static/red.png"},
					{checked:false,side:'n',url:"/static/blue.png"},
					{checked:false,side:'n',url:"/static/blue.png"},
					{checked:false,side:'n',url:"/static/blue.png"},
				],
				start_flag:false,
				now_side:"n",
				aaR: "红方先",
				aaB: "蓝方先",
				isStarted: false,
				isEndded : false,
 			}
 		},
 		methods: {
 			change(e) {
 				var i =e.detail.index;
				if(this.isEndded)
				{
					getApp().globalData.ShowToast("本局已经结束，点击‘重新开始’按钮再开一局!")
					retutn;
				}
				if(this.start_flag)
				{
					if(this.now_side=='R'&&this.items[i].side=='n')
					{
						this.now_side = 'B'
						this.items[i]
						this.items[i].url = red_url
						this.items[i].checked = true
						this.items[i].side='R'
					}
					else if(this.now_side=='B'&&this.items[i].side=='n')
					{
						this.now_side = 'R'
						this.items[i].url = blue_url
						this.items[i].checked = true
						this.items[i].side='B'
					}
					else
					{
						
					}
					//裁决是否获胜
					var win =false
					var s = this.items
					var a,b,c
					a=0;b=1;c=2;win = s[a].side==s[b].side&&s[b].side==s[c].side&&s[a].side!='n';if(win){if(s[a].side=='R'){getApp().globalData.ShowToast("红方获胜")}else{getApp().globalData.ShowToast("蓝方获胜")}this.clear_2();return}
					a=3;b=4;c=5;win = s[a].side==s[b].side&&s[b].side==s[c].side&&s[a].side!='n';if(win){if(s[a].side=='R'){getApp().globalData.ShowToast("红方获胜")}else{getApp().globalData.ShowToast("蓝方获胜")}this.clear_2();return}
					a=6;b=7;c=8;win = s[a].side==s[b].side&&s[b].side==s[c].side&&s[a].side!='n';if(win){if(s[a].side=='R'){getApp().globalData.ShowToast("红方获胜")}else{getApp().globalData.ShowToast("蓝方获胜")}this.clear_2();return}
					a=0;b=3;c=6;win = s[a].side==s[b].side&&s[b].side==s[c].side&&s[a].side!='n';if(win){if(s[a].side=='R'){getApp().globalData.ShowToast("红方获胜")}else{getApp().globalData.ShowToast("蓝方获胜")}this.clear_2();return}
					a=1;b=4;c=7;win = s[a].side==s[b].side&&s[b].side==s[c].side&&s[a].side!='n';if(win){if(s[a].side=='R'){getApp().globalData.ShowToast("红方获胜")}else{getApp().globalData.ShowToast("蓝方获胜")}this.clear_2();return}
					a=2;b=5;c=8;win = s[a].side==s[b].side&&s[b].side==s[c].side&&s[a].side!='n';if(win){if(s[a].side=='R'){getApp().globalData.ShowToast("红方获胜")}else{getApp().globalData.ShowToast("蓝方获胜")}this.clear_2();return}
					a=0;b=4;c=8;win = s[a].side==s[b].side&&s[b].side==s[c].side&&s[a].side!='n';if(win){if(s[a].side=='R'){getApp().globalData.ShowToast("红方获胜")}else{getApp().globalData.ShowToast("蓝方获胜")}this.clear_2();return}
					a=2;b=4;c=6;win = s[a].side==s[b].side&&s[b].side==s[c].side&&s[a].side!='n';if(win){if(s[a].side=='R'){getApp().globalData.ShowToast("红方获胜")}else{getApp().globalData.ShowToast("蓝方获胜")}this.clear_2();return}
					for(var i=0;i<this.items.length;i++)
					{
						if(this.items[i].side=='n')
							break;
					}
					if(i==9)
						this.noWin();
				}
				else
				{
					getApp().globalData.ShowToast("确定先方然后在开始游戏!")
				}
 			},
			noWin() {
				this.start_flag = false
				this.isEndded = true
				this.now_side = 'n'
				getApp().globalData.ShowToast("平局")
			},
			Restart() {
				for(var i=0;i<this.items.length;i++)
				{
					this.items[i].checked = false
					this.items[i].side='n'
				}
				this.start_flag = false
				this.isStarted=false
				this.isEndded =false
				this.now_side = 'n'
				this.aaR = '红方先'
				this.aaB = "蓝方先"
			},
			clear_2() {
				for(var i=0;i<this.items.length;i++)
				{
					// this.items[i].checked = false
					this.items[i].side=i+'1'
				}
				this.start_flag = false
				this.isEndded = true
				this.now_side = 'n'
			},
			start(e) {
				if(this.isStarted)
				{
					
				}
				else 
				{
					this.start_flag = true
					this.now_side = e
					
					this.aaR = '红方'
					this.aaB = "蓝方"
					this.isStarted = true
					getApp().globalData.ShowToast("游戏开始")
				}
					
			}
 		}
 	}
 </script>
 
 <style>
	.grid-item-box {
			flex: 1;
			/* position: relative;
	*/
			/* #ifndef APP-NVUE */
			display: flex;
			/* #endif */
			flex-direction: column;
			align-items: center;
			justify-content: center;
			padding: 15px 0;
		}
	.grid-1{
		margin-top: 20rpx;
		margin-left: 20rpx;
		margin-right: 20rpx;
	}
	.active{
		background-color: #09BB07;
	}
	.image {
		width: 150rpx;
		height: 150rpx;
	}
	.c-2{
		margin: 0 auto;
		margin-top: 175rpx;
		margin-bottom: 50rpx;
		width: 60%;
	}
	.c-3{
		margin: 0 auto;
		margin-top: 50rpx;
		margin-bottom: 50rpx;
		width: 60%;
	}
	.c-4{
		margin: 0 auto;
		margin-top: 160rpx;
		margin-bottom: 0rpx;
		width: 100%;
	}
 </style>