<template>
	<view>
		<!-- #ifdef MP -->
			<!-- 小程序端导航栏 -->
			<view class="flex align-center fixed-top" style="height: 44px;">
				<!-- 搜索框 -->
				<view class="flex align-center flex-1 rounded-circle ml-2 px-1" style="background-color: #F6F7F8; color:#959FA0;">
					<text class="iconfont iconsousuokuang"></text>
					<text>音乐MV专辑：繁华梦</text>
				</view>
				<view class="flex align-center px-2" style="color:#959FA0;">分类</view>
			</view>
			<view style="height:44px;"></view>
		<!-- #endif -->
		<!-- 轮播图组件 -->
		<view class="px-3 py-2">
			<swiper-dot :info="swipers" :current="current">
				<!-- 轮播图 -->
				<swiper circular :autoplay="true" :interval="3000" :duration="150" style="height: 250rpx;"
				:current="current" @change="changeSwiper">
					<swiper-item v-for="(item,index) in swipers" :key="index">
						<image :src="item.src" mode="aspectFill" style="height:250rpx;width: 100%;" class="rounded-lg"></image>
					</swiper-item>	
				</swiper>
			</swiper-dot>
		</view>
		<!-- 卡片组件 -->
		<card title="为你推荐">
			<!-- 列表组件1 -->
			<view class="f-list">
				<view v-for="i in 6" :key="i" @click="openDetailVideo" style="margin-left:15rpx;margin-right: 15rpx; min-height: 5rpx;width: 328rpx;" class="rounded-lg border position-relative mb-2">
					<!-- 播放图片 -->
					<image src="/static/demo/list2/01.jpg" style="width:100%;height:220rpx;" mode="aspectFill" class="rounded-top-lg"></image>
					<!-- 播放量 -->
					<view style="height: 65rpx; top:155rpx; background-image: linear-gradient(to bottom,rgba(0,0,0,0),rgba(0,0,0,0.8));" class="flex align-center text-white position-absolute left-0 right-0">
						<text class="iconfont iconbofangshu font-md mx-1"></text>
						<text class="font-sm">200.1万</text>
						<text class="iconfont icondanmushu font-md mx-1"></text>
						<text class="font-sm">7700</text>
					</view>
					<!-- 底部说明 -->
					<view class="px-1 pb-1">
						<!-- 标题 -->
						<view class="font">
							标题
						</view>
						<!-- 分类 -->
						<view class="flex align-center justify-between text-light-muted">
							<text class="font">MV</text>
							<text class="iconfont icongengduo"></text>
						</view>
					</view>
				</view>
			</view>
		</card>
		<view class="f-divider"></view>
		<card title="为你推荐">
			<!-- 列表组件2 -->
			<view class="f-list">
				<view v-for="i in 6" :key="i" style="margin-left:15rpx;margin-right: 15rpx; min-height: 5rpx;width: 210rpx;" class="rounded-lg position-relative mb-2 rounded-lg">
					<!-- 播放图片 -->
					<image src="/static/demo/list3/1.webp" style="width:100%;height:280rpx;" mode="aspectFill" class="rounded-lg"></image>
					<!-- 播放量 -->
					<view style="height: 65rpx; top:215rpx; background-image: linear-gradient(to bottom,rgba(0,0,0,0),rgba(0,0,0,0.8));" class="flex align-center text-white position-absolute left-0 right-0">
						<text class="iconfont iconbofangshu font-md mx-1"></text>
						<text class="font-sm">200.1万</text>
						
					</view>
					<!-- 标题 -->
					<view class="font">标题</view>
				</view>
			</view>
		</card>
		<view class="f-divider"></view>
		<card title="为你推荐">
			<!-- 列表组件3 -->
				<view class="f-list">
					<media-list v-for="(item,index) in list3" :key="index" :item="item" :index="index"></media-list>
				</view>
		</card>
		</view>
</template>

<script>
	import swiperDot from '@/components/common/swiper-dot.vue';
	import card from '@/components/common/card.vue';
	import mediaList from '@/components/common/media-list.vue';
	export default {
		components:{
			swiperDot,
			card,
			mediaList
		},
		data() {
			return {
				current:0,
				swipers:[{
					src:"/static/demo/swiper/1.jpg",
					title:"四六级如何才能轻松闯关？"
				},{
					src:"/static/demo/swiper/2.jpg",
					title:"吉娜专访：首次公开腰围，郎朗也是我粉丝！！！"
				},{
					src:"/static/demo/swiper/3.jpg",
					title:"30天VLOG挑战，投稿瓜分50万奖金。"
				}],
				list3:[{
					cover:"/static/demo/list2/02.jpg",
					title:"烟雨风缥缈可可爱爱没有脑袋可可爱爱没有脑袋",
					create_time:"今天07:00",
					play_count:"200.1万",
					danmu_count:"7700"
				},{
					cover:"/static/demo/list2/02.jpg",
					title:"烟雨风缥缈可可爱爱没有脑袋可可爱爱没有脑袋",
					create_time:"今天07:00",
					play_count:"200.1万",
					danmu_count:"7700"
				},{
					cover:"/static/demo/list2/02.jpg",
					title:"烟雨风缥缈可可爱爱没有脑袋可可爱爱没有脑袋",
					create_time:"今天07:00",
					play_count:"200.1万",
					danmu_count:"7700"
				}]
			}
		},
		onLoad() {

		},
		onNavigationBarSearchInputClicked(){
			console.log('点击了搜索框');
		},
		onNavigationBarButtonTap(e){
			console.log('点击了按钮');
		},
		methods: {
			changeSwiper(e){
				this.current = e.detail.current;
			},
			openDetailVideo(){
				uni.navigateTo({
					url:"../detail-video/detail-video"
				})
			}
		}
	}
</script>

<style>
	.f-list{
		display:flex;
		flex-wrap: wrap;
		padding-left: 15rpx;
		padding-right: 15rpx;
	}
</style>
