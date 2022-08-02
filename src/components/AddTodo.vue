<template>
    <div>
        <form v-on:submit="AddTodo">
            <input type="text" v-model="title" name="title" placeholder="Add todo...">
            <input type="submit" value="Submit" class="btn">
        </form>
    </div>
</template>

<script>
export default{

    name: "AddTodo",
    data(){
        return{
            title:''
        }
    },
    methods: {
        AddTodo(e){
                e.preventDefault();
                const newTodoList = {
                    id: 4,
                    title: this.title,
                    completed:false
                        
                    
                }
                //send via emmit
                this.$emit('add-Todo', newTodoList);
                this.title = '';
        }
    }
}
</script>

<style>
    form{
        display: flex;
    }
    input[type="text"]{
        flex:10;
        padding:5px;
    }
    input[type="button"]{
        flex:2;

    }


</style>