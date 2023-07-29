<template>
    <div class="todo">
        <ul>
            <TodoItem
            v-for="(todo, index) in todos" :key="todo.id"
            v-bind:todo="todo"
            v-bind:index="index"
            v-on:remove-todo="removeTodo"
            />
        </ul>
    </div>
</template>


<script>
import TodoItem from "@/components/TodoItem"
export default {
    props: ['todos'],
    components: {
        TodoItem
    },
    methods: {
        removeTodo(id){
            this.$emit('remove-todo', id)
        }
    }
}
</script>

<style scoped>

    .todo{
        display: flex;
        justify-content: center;
    }

    ul {
       width: 40%;
        list-style: none;
        margin: 0;
        padding: 0;
    }
</style>