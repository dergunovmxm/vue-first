<template>
    <form @submit.prevent="onSubmit">
        <input type="text" v-model="title">
        <button type="submit">+</button>
    </form>
</template>

<script>
export default {
    data() {
        return {
            title: ''
        }
    },
    methods: {
        onSubmit() {
            if(this.title.trim()){
                const newTodo = {
                    id: Date.now(),
                    title: this.title,
                    completed: false
                }
                this.$emit('add-todo', newTodo)
                this.title = ''
            }
        }
    }
}
</script>

<style >
form {

    display: flex;
    justify-content: center;
}

button {
    background-color: white;
    border-radius: 8px;
    border: 3px solid #80FF80;
    width: 50px;
    color: #80FF80;
    font-size: 32px;
}

input {
    padding: 15px;
    border-radius: 8px;
    margin-right: 10px;
    width: 20%;
}
</style>