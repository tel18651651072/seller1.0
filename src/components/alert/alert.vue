<template>
	<div class="alert">
		<h1 class="title">温馨提醒</h1>
		<p class="content">您应结算￥{{amount}}元</p>
		<div class="footer">
			<a v-link="" class="statement">去结算</a>
			<span class="stay" @click="alertClose">再看看</span>
		</div>

	</div>
</template>
<script type="text/ecmascript-6">
	export default {
	   props:{
	     amount:{
            type: Number
	     }
	   },
	   methods:{
	     alertClose(event) {
	        this.$dispatch('alert.close',event.target);
	     }
	   }
	};
</script>
<style lang="stylus" rel="stylesheet/stylus">
     @import '../../common/stylus/mixin.styl';
	.alert{
		position: fixed;
		bottom: 350px;
		left: 50%;
		margin-left: -100px;
		width: 200px;
		box-sizing: border-box;
		border-1px(7,17,27,0.5);
		box-shadow: 0 4px 8px 0 rgba(0,0,0,0.6); 
		font-size: 0;
		z-index: 60;
		border-radius: 5px;
		overflow: hidden;
		.title{
			height: 30px;
			line-height: 30px;
			font-size: 14px;
			background: #00a0dc;
			color: #fff;
			text-align: center;
		}
		.content{
			text-align: center;
			background: #fff;
			font-size: 12px;
			height: 60px;
			padding: 10px;
			border-bottom: 1px solid rgba(0,0,0,0.3);
		}
		.footer{
			display: flex;
			font-size: 14px;
			height: 30px;
			line-height: 30px;
			background: #f3f5f7;
            .statement{
               display: inline-block;
               flex:1;
               text-align: center;
               border-right:1px solid rgba(0,0,0,0.3);
            }
            .stay{
               display: inline-block;
               flex:1;
               text-align: center;
               color: #7e8c8d;
            }
		}
	}
</style>