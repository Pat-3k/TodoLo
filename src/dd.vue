<template>
<div id="app">
  <HeaderItem v-on:add-Todo="HeaderItem"/>
  <AddTodo v-on:add-Todo="AddTodo"/>
  <TodoList v-bind:TodoList="TodoList" v-on:del-todo="deleteTodo"/>
</div>
</template>

<script>  
import TodoList from './components/TodoList.vue';
import AddTodo from './components/AddTodo.vue';
import HeaderItem from './components/layout/HeaderItem';
import axios from 'axios';
export default {
  name: 'App',
  components: {
    TodoList,
    AddTodo,
    HeaderItem,
},
data(){
  return{
    TodoList: []
  }
},
  methods:{
    deleteTodo(id)
    {
      axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
      .then()
      .catch()
      //this.TodoList = this.TodoList.filter(TodoList => TodoList.id !== id);
    },
   
   AddTodo(newTodoList){
    const {title, completed} = newTodoList;
    axios.post('https://jsonplaceholder.typicode.com/todos',{
      title,
      completed
    })
    .then(res => this.TodoList = [...this.TodoList, res.data])
    .catch(error=> {
      return Promise.reject(error);
       
    })
    }},

   created(){
    axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5')
    .then (res => this.TodoList = res.data)
    .catch(error=>{
      return Promise.reject(error);
    })
   }
  
}


</script>

<style>
 *{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  
}
body{
  font-family: Arial, Helvetica, sans-serif
}
.btn{
  display: inline;
  border: none;
  background-color: #555;
  color: #fff;
  padding: 7px 20px;
  cursor: pointer;

}
.btn:hover{
  background-color: #666;
}
</style>
