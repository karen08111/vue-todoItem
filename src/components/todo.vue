<template>
	<div>
		<p>
			<button v-for="item in newList" :key="item.state" @click="select(item.state)">{{item.text}}</button>
			
			
			
			
		</p>	
	</div>
</template>

<script>
	export default{
		props:{
			todolist:{
				type:Array
			},
			state: {
				type: String
			}
		},
		data(){
			return{
				newList:[{
					state: 'all',
					text: '显示全部'
				},{
					state: 'active',
					text: '显示未选'
				},{
					state: 'cmpleted',
					text: '显示已选'
				}],
				
			}
		},
		methods:{
			select(state){
				this.$emit('sle', state);
			}
		}
	}
</script>

<style scoped>
	
</style>