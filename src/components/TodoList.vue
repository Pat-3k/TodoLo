<template>
    <div>
        <div v-bind:key="TodoList.id" v-for="TodoList in TodoList">
            <TodoItem v-bind:TodoList="TodoList" v-on:del-todo="$emit('del-todo', TodoList.id)"/>
        </div>

    </div>
</template>

<script>

import TodoItem from './TodoItem.vue';


export default{
name:'TodoList',
components:{
    
    TodoItem
},
props: ["TodoList"]


}

</script>

<style>



</style>