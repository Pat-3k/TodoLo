<template>
    <div class="todo-item" v-bind:class="{'is-complete':TodoList.completed}">
        <p>
            <input type="checkbox" v-on:change="markComplete" v-bind:checked="TodoList.completed"/>
            {{TodoList.title}}
            <button v-on:click="$emit('del-todo', TodoList.id)" class="del">x</button>
        </p>
    </div>
</template>

<script>
export default{
    name:"TodoItem",
    props:["TodoList"],

    data(){
        return{
            Todo: this.TodoList
        }
    },
    methods:{
        markComplete(){
            this.Todo.completed = !this.Todo.completed;

        }
    }

}

</script>

<style scoped>
    .todo-item{
        background-color: peachpuff;
        padding: 10px;
        border-bottom: 1px #ccc dotted;
    }
    .is-complete{
        text-decoration: line-through;
    }
    .del{
        background-color: antiquewhite;
        color:black;
        border: none;
        padding: 5px 9px;
        border-radius: 50%;
        cursor: pointer;
        float: right;
    }
</style>