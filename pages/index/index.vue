<!-- <template>
	<web-view src="/hybrid/html/a.html?data=123" @message="message"></web-view>
</template>

<script>
	var NfcAdapter;
	var NdefRecord;
	var NdefMessage;

	export default {
		onLoad() {

		},
		methods: {
			message(event) {
				console.log('接受webview传递过来的数据:' + event.detail.data);
			}
		}
	}
</script>

<style scoped>

</style>
 -->
 
 <template>
 	<div>
		<button type="primary" @click="btnGo">跳转nfc界面</button>
		<button type="primary" @click="listen">开启监听</button>
		<text>{{tag}}</text>
 	</div>
 </template>
 
 <script>
 	export default {
		data() {
			return {
				tag: "等待tag"
			}
		},
		methods: {
			btnGo() {
				uni.navigateTo({
					url:'/pages/nfc/nfc'
				})
			},
			listen(e){
				var _this = this;
				//监听事件
				_this.$eventHub.$on('fire',function(data){
					console.log('>>>> fire data:',data);
					_this.tag=data;
				});
			}
			
		},
 	}
 </script>
 
 <style scoped>
 
 </style>