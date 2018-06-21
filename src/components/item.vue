<template>
	<div>
		<li>
			<span @click="hand(lid)"><span class="wei" v-if="bol.length==0">未选</span><span class="yi" v-if="bol.length>0">已选</span> </span>  &nbsp;&nbsp;&nbsp;{{val}}<button @click="del(lid)">删除</button>
		</li>
	</div>
</template>

<script>
	export default{
		props:{
			lists:{
				type:Array
			},
			val:{
				type:String
			},
			lid:{
				type:Number
			},
			bol:{
				type:String
			}
		},
		methods:{
			hand(data){
				let l = this.lists.findIndex((value)=>{
					return value.lid==data;
				})
				this.$emit('state',l);
			},
			del(data){
				let i = this.lists.findIndex((value,index,arr)=>{
					return value.lid==data;
				})
				this.$emit('dels',i);
			}
		}
	}
</script>

<style>
	li{
		list-style: none;
	}
	.yi{
		color: green;
		cursor: pointer;
	}
	.wei{
		color: red;
		cursor: pointer;
	}
</style>