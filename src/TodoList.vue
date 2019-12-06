<template>
	<div>
		<ul>
		
		 <app-todoItem
		 	v-for="(todo, i) in todos"
		 	v-bind:todo="todo"
		 	v-bind:index="i"
		 	v-on:remove-todo="removeTodo"
		 ></app-todoItem>
		
		</ul>
	</div>
</template>
<script>
import TodoItem from './Todoitem'
	export default{
		props:['todos'],
		data(){
			return{
				
			}
		},
		components:{
			'app-todoItem': TodoItem
		},
		methods:{
			removeTodo(id){
				this.$emit('remove-todo', id)
			}
		}
	}
</script>
<style scoped>
	ul{
		list-style:none;
		margin:0;
		padding:0;
	}

</style>