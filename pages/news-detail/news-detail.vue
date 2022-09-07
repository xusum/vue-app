<template>
	<view class="news_detail">
		<text class="title">{{detail.title}}</text>
		<view class="info">
			<text>发表时间：{{detail.add_time | fromatDate}}</text>
			<text>浏览：{{detail.click}}</text>
		</view>
		<view class="content">
			<rich-text :nodes="detail.content"></rich-text>
			<!-- {{detail.content}} -->
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				id: 0,
				detail:{}
			}
		},
		methods: {
			async getNewsDetail (){
				const res = await this.$myRuquest({
					url:'/api/getnew/'+this.id
				})
				// console.log(res)
				this.detail = res.data.message[0]
			}
		},
		onLoad(options){
			// console.log(options)
			this.id = options.id
			this.getNewsDetail()
		}
	}
</script>

<style lang="scss">
	.news_detail{
		font-size: 30rpx;
		padding:  0 20px;
		.title{
			text-align: center;
			display: block;
			width: 710rpx;
			margin: 20rpx 0;
		}
		.info{
			display: flex;
			justify-content: space-between;
			
		}
	}
</style>
