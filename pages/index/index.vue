<template>
<!-- 	<div>
		<button type="primary" @click="listenNFCStatus">listenNFCStatus</button>
	</div> -->
	<web-view src="/hybrid/html/a.html"></web-view>
</template>

<script>
	var NfcAdapter;
	var NdefRecord;
	var NdefMessage;

	export default {
		onLoad() {
			// this.listenNFCStatus();
		},
		methods: {
			test1(){
				plus.android.importClass("")
			},
			listenNFCStatus() {
				try {
					var main = plus.android.runtimeMainActivity();
					var Intent = plus.android.importClass('android.content.Intent');
					var Activity = plus.android.importClass('android.app.Activity');
					var PendingIntent = plus.android.importClass('android.app.PendingIntent');
					var IntentFilter = plus.android.importClass('android.content.IntentFilter');
					NfcAdapter = plus.android.importClass('android.nfc.NfcAdapter');
					var nfcAdapter = NfcAdapter.getDefaultAdapter(main);
					var intent = new Intent(main, main.getClass());
					intent.addFlags(Intent.FLAG_ACTIVITY_SINGLE_TOP);
					var pendingIntent = PendingIntent.getActivity(main, 0, intent, 0);
					var ndef = new IntentFilter("android.nfc.action.TECH_DISCOVERED");
					ndef.addDataType("*/*");
					var intentFiltersArray = [ndef];
					var techListsArray = [
						["android.nfc.tech.IsoDep"],
						["android.nfc.tech.NfcA"],
						["android.nfc.tech.NfcB"],
						["android.nfc.tech.NfcF"],
						["android.nfc.tech.Nfcf"],
						["android.nfc.tech.NfcV"],
						["android.nfc.tech.NdefFormatable"],
						["android.nfc.tech.MifareClassi"],
						["android.nfc.tech.MifareUltralight"]
					];
					// console.log("nfcadapter:"+nfcAdapter);
					
					// document.addEventListener("newintent",
					// 	function() {
					// 		console.error('newintent');
					// 		setTimeout(handle_nfc_data1, 1000);
					// 	}, false);
					// document.addEventListener("pause", function(e) {
					// 	if (nfcAdapter) {
					// 		nfcAdapter.disableForegroundDispatch(main);
					// 		console.log('pause');
					// 	}
					// }, false);
					// document.addEventListener("resume", function(e) {
					// 	if (nfcAdapter) {
					// 		console.log('resume');
					// 		nfcAdapter.enableForegroundDispatch(main, pendingIntent, intentFiltersArray, techListsArray);
					// 	}
					// }, false);
					// nfcAdapter.enableForegroundDispatch(main, pendingIntent, intentFiltersArray, techListsArray);
				} catch (e) {
					// console.error(e);
				}
			}
		}
	}
</script>

<style scoped>

</style>
