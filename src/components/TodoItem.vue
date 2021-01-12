<template>
    <div class="todo-item" v-bind:class="{'is-complete':todo.completed}">
    <p>
        <input type="checkbox"  v-on:change="markComplete">
        {{todo.title}}
        <button @click="$emit('del-todo', todo.id)" class="del">X</button>
        </p>
    </div>
</template>

<script>
export default {
    name: "TodoItem",
    props: ["todo"],
    methods:{
        markComplete(){
            this.props.todo.completed = !this.props.todo.completed;
        }
    }
}
</script>

<style scoped>
    .todo-item{
        background:#f4f4f4;
        padding:10px;
        border-bottom:1px #ccc solid;
    }

    .is-complete{
        text-decoration: line-through;
    }

    .del{
        background: #f00;
        color:#fff;
        padding:5px 9px;
        border-radius: 50%;
        cursor: pointer;
        float: right;
    }
</style>