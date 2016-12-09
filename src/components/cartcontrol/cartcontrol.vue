<template>
	<div class="cartcontrol">
		<div class="cart-decrease" v-show="food.count>0" @click.stop.prevent="decreaseCart" transition="move">
		     <i class="inner icon-remove_circle_outline"></i>
		</div>
		<div class="cart-count"  v-show="food.count>0">{{food.count}}</div>
		<div class="cart-add icon-add_circle" @click.stop.prevent="addCart"></div>
	</div>
</template>
<script type="text/ecmascript-6">
    import Vue from 'vue';
	export default {
	   props:{
	     food:{
	       type:Object
	     }
	   },
	   created() {

	   },
	   methods:{
	     addCart(event) {
	        if (!event._constructed) {
	           return
	        }
	        console.log('click');
	        if (!this.food.count) {
	           /* this.food.count=1; 这里不存在的属性需要使用vue添加*/
	           Vue.set(this.food,'count',1);
	        } else {
	           this.food.count ++;
	        }
	        this.$dispatch('cart.add',event.target);
	     },
         decreaseCart(event) {
            if (!event._constructed) {
	           return
	        }
	        if (this.food.count>=1) {
	           this.food.count--
	        } 
         }
	   }
	};
</script>
<style lang="stylus" rel="stylesheet/stylus">
	.cartcontrol{
		font-size: 0;
		.cart-decrease{
			display: inline-block;
			padding: 6px;
			transition: all 0.4s linear;
			&.move-transition{
				opacity: 1;
				transform:translate3D(0,0,0);
				.inner{
					display: inline-block;
					line-height: 24px;
					font-size: 24px;
					color:rgb(0,160,220);
					transition: all 0.4s linear;
					transform: rotate(0);
				}
			}
			&.move-enter,&.move-leave{
				opacity: 0;
				transform:translate3D(24px,0,0);
				.inner{
					transform: rotate(180deg);
				}
			}
		}
		.cart-count{
			vertical-align: top;
			width: 12px;
			padding-top: 6px;
			text-align: center;
			color: rgb(147,153,159);
			display: inline-block;
			font-size: 10px;
			line-height: 24px;
		}
		.cart-add{
			display: inline-block;
			line-height: 24px;
			font-size: 24px;
			padding: 6px;
			color:rgb(0,160,220);
		}
	}
</style>