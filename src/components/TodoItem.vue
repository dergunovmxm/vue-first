<!-- eslint-disable vue/no-mutating-props -->
<template>
    <li>
        <span v-bind:class="{ done: todo.completed }">
            <input type="checkbox" class="custom-checkbox" v-on:change="todo.completed = !todo.completed">
            <strong>{{ index + 1 }}</strong>
            {{ todo.title }}
        </span>
        <button class="remove-button" v-on:click="$emit('remove-todo', todo.id)">&times;</button>

    </li>
</template>

<script>
export default {
    props: {
        todo: {
            type: Object,
            required: true
        }, 
        index: Number
    }
}
</script>


<style scoped>
.custom-checkbox {
    border: 1px soled cornflowerblue;
    width: 20px;
    height: 20px;
}

.custom-checkbox:not(:disabled):not(:checked)+label:hover::before {
    border-color: red;
}

span {
    font-size: 18px;
    display: flex;
    justify-content: center;
    align-items: center;
}

input {
    margin-right: 1rem;
}

strong {
    margin-right: 0.5rem;
}

li {
    border: 1px solid black;
    border-radius: 8px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin: 10px;
    padding: 15px;
}

.remove-button {
    background-color: white;
    border: 1px solid red;
    color: red;
    border-radius: 4px;
    font-size: 18px;
    cursor: pointer;
    width: 20px;
    height: 20px;
    display: flex;
    justify-content: center;
    align-items: center;
}

.done {
    text-decoration: line-through;
}
</style>
