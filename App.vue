<script>
export default {
	onLaunch: function() {
		
	},
	onShow: function() {
		
	},
	onHide: function() {
		
	},
	globalData: {
		ShowToast: function(msg,time) {     //在其他页面时调用  getApp().globalData.ShowToast(  )
			uni.showToast({
			    title: msg,
			    duration: time,
				icon:'none',
			});
		},
	}
};
</script>

<style>


</style>
