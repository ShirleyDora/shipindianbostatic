<template>
	<view>
		<navigator url="../user-space/user-space">
		<view class="p-3 flex align-center" >
			<image src="/static/demo/6.jpg" style="height:120rpx;width:120rpx;" class="bg-light rounded-circle flex-shrink" mode="aspectFill"></image>
			<view class="flex flex-column pl-3 flex-1">
				<view class="font-md text-dark">
					shirley
					<text class="font-sm text-muted ml-3">女 武汉</text>
				</view>
				<text class="font-sm text-muted">萌萌哒！</text>
			</view>
		</view>
		</navigator>
		<view class="f-divider"></view>
		<f-list-item icon="iconshipin" title="我的作品" :showRightIcon="false" rightText="26个"
		@click="navigateTo('user-video')"></f-list-item>
		<f-list-item icon="iconshoucang1" title="收藏"
		@click="navigateTo('user-fava')"></f-list-item>
		<f-list-item icon="iconguanzhu" title="关注" rightText="365"></f-list-item>
		<f-list-item icon="iconlishi" title="历史记录"></f-list-item>
		<view class="f-divider"></view>
		<view class="py-2 px-3">
			<main-big-button @click="addMsg">立即投稿</main-big-button>
		</view>
		<!-- 弹框 -->
		<f-popup ref="popup">
			<view class="position-absolute bottom-0 left-0 right-0 bg-white animate__animated animate__faster animate__fadeIn">
				<view class="flex" style="height: 200rpx;">
					<view class="flex-1 flex align-center justify-center flex-column" hover-class="bg-light"
					@click="navigateTo('create')">
						<text class="iconfont icondingdanwenjian flex align-center justify-center text-white bg-primary rounded-circle" style="width: 80rpx;height: 80rpx;"></text>
						<text class="font mt-1 text-muted">单集</text>
					</view>
					<view class="flex-1 flex align-center justify-center flex-column" hover-class="bg-light">
						<text class="iconfont icon918caidan_wenjian flex align-center justify-center text-white bg-main rounded-circle" style="width: 80rpx;height: 80rpx;"></text>
						<text class="font mt-1 text-muted">连载</text>
					</view>
				</view>
				<view class="f-divider"></view>
				<view class="py-2 flex align-center justify-center font-md text-muted" hover-class="bg-light" @click.stop="hidePopup">取消</view>
			</view>
		</f-popup>
		
	</view>
</template>

<script>
	import fListItem from '@/components/common/f-list-item.vue'
	import mainBigButton from '@/components/common/main-big-button.vue';
	import fPopup from '@/components/common/f-popup.vue';
	export default {
		components:{
			fListItem,
			mainBigButton,
			fPopup
		},
		data() {
			return {
				show:false,
			}
		},
		methods: {
			//选择投稿类型
			addMsg(){
				this.$refs.popup.show();
			},
			hidePopup(){
				this.$refs.popup.hide();
			},
			navigateTo(path){
				uni.navigateTo({
					url: '/pages/'+path+'/'+path,
				});
			}
		}
	}
</script>

<style>

</style>
