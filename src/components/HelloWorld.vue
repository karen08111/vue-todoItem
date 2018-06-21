<template>
  <div class="hello">
		<input type="text" v-model="value" @keyup.enter="add()"  />
		<input type="submit" @click="add()"/>
		<item v-for="(i,key,index) in full" :val="i.zhi" :bol="i.bol" :lid="i.lid" :key="i.lid" :lists="list" @dels="hand" @state="sta"></item>
		<p v-if="full.length==0">空的</p>
		<todo :todolist="list" :state="state" @sle="toggle"></todo>	
		<button @click="clear">清空所有</button>
  </div>
</template>

<script>
		import item from '@/components/item'
		import todo from '@/components/todo'
export default {
  name: 'HelloWorld',
  components:{
  	item,
  	todo
  },
  data () {
    return {
      value: '',
      num:0,
      list:[],
      newList:[],
      state: 'all'
    }
  },
  methods:{
	  	add(){
	  		let obj={
	  			lid:this.num+=1,
	  			zhi:this.value,
	  			bol:''
	  		}
	  		this.list.push(obj);
	  		this.lsit=this.list.reverse();
	  		this.value='';
	  	},
	  	hand(i){
	  		this.list.splice(i,1);//删除
	  	},
	  	sta(l){
	  		if(this.list[l].bol){
	  			this.list[l].bol='';
	  		}else{
	  			this.list[l].bol='1';//改变选中状态
	  		}
	  	},
			clear(){
				this.list=[];
				this.state='all';
			},
			toggle (state) {
				this.state = state
			}
	 },
	 computed:{
	 		full(){
	 			if (this.state === 'all') {
	 				return this.list
	 			}else if(this.state === 'active'){
	 				const completed = this.state === 'completed' ? '1' : ''
	 				return this.list.filter(x=> x.bol === completed);//返回没有选中的
	 			}else if(this.state==='cmpleted'){
	 				const completed = this.state === 'completed'?'':'1';
	 				return this.list.filter(x=> x.bol === completed)//返回已经选中的
	 			}
	 		}
	 }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
