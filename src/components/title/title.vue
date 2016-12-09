<template>
	<div class="v-title">
		<div class="line"></div>
		<div class="text">{{msg}}</div>
		<div class="line"></div>
	</div>
</template>
<script type="text/ecmascript-6">
	export default {
	  props:{
	     msg:{
	       type:String
	     }
	  }
	};
</script>
<style lang="stylus" rel="stylesheet/stylus">
	.v-title{
		width: 80%;
		margin:28px auto 24px auto;
		display: flex;
		.line{
			flex:1;
			position: relative;
			top: -6px;
			border-bottom: 1px solid rgba(255,255,255,0.2);
		}
		.text{
		   font-weight: 700;
           padding: 0 12px;
           font-size: 14px; 
		}
	}
</style>