<template>
	<view>
		<button @click="writeData()">writeData</button>
		<button @click="readData()">readData</button>
	</view>
</template>

<script>
	import nfc from '../../utils/hexiii-nfc.js'
	export default {
		data() {
			return {

			}
		},
		onLoad: function(){
			nfc.listenNFCStatus();
		},
		methods: {
			writeData(){
				uni.showModal({
					title: "温馨提示",
					content: "此操作将抹除芯片中的数据，且不可逆",
					success: function (res) {
						if (res.confirm) {
						   nfc.writeData();
						} 
					}
				})
			},
			readData(){
				nfc.readData();
			},
			
		}
	}
</script>

<style>

</style>
