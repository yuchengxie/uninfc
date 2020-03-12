<template>
	
	<view class="">
		<web-view :src="url" @message="message"></web-view>
		<button type="primary" @click="goIndex">go index</button>
	</view>
</template>

<script>
	var NfcAdapter;
	var NdefRecord;
	var NdefMessage;

	export default {
		onLoad() {

		},
		data() {
			return {
				url: '/hybrid/html/a.html?data=123',
				tag:''
			}
		},
		methods: {
			message(event) {
				var tagData=JSON.stringify(event.detail.data);
				console.log('接受webview传递过来的数据:' + tagData);
				// uni.setStorageSync("tag",tagData);
				// this.tag = tagData;
				this.$eventHub.$emit('fire',tagData);
			},
			goIndex(){
				uni.navigateTo({
					url:"../index/index",
				})
			}
		}
	}
</script>

<style scoped>

</style>
