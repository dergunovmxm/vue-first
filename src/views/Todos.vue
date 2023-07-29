<!-- eslint-disable vue/return-in-computed-property -->
<template>
    <div >
      <h2>ToDo List</h2>
      <router-link to="/">Homepage</router-link>
      <br/>
      <br/>
      <AddTodo @add-todo="addTodo"/>
      <br/>
      <select v-model="filter">
        <option value="all">Все</option>
        <option value="completed">Завершенные</option>
        <option value="inprogress">В процессе</option>
      </select>
      <br/>
      <Loader v-if="loading"/>
      <TodoList  v-else-if="filteredTodos.length" v-bind:todos="filteredTodos" v-on:remove-todo="removeTodo"/>
      <EmptyTodos v-else />
    </div>
  </template>
  
  <script>
  import TodoList from '@/components/TodoList'
  import AddTodo from '@/components/AddTodo'
  import EmptyTodos from '@/components/EmptyTodos'
  import Loader from '@/components/Loader'

  export default {
    name: 'App',
    data() {
      return {
        todos: [],
        loading: true,
        filter: 'all'
      }
    },
    components: {
      TodoList,
      AddTodo,
      EmptyTodos,
      Loader
    },
  
    mounted() {
      fetch('https://jsonplaceholder.typicode.com/todos?_limit=5')
        .then(response => response.json())
        .then(json => {
            this.todos = json
            this.loading = false 
        })
    },

    // watch: {
    //     filter(value){
    //         console.log(value)
    //     }
    // },

    computed: {
        // eslint-disable-next-line vue/return-in-computed-property
        filteredTodos(){
            if(this.filter === 'all') {
                return this.todos
            }
            if(this.filter === 'completed') {
                return this.todos.filter((todo) => todo.completed)
            }
            if(this.filter === 'inprogress') {
                return this.todos.filter((todo) => !todo.completed)
            }
        }
    },
    methods:{
        removeTodo(id){
          this.todos = this.todos.filter(t => t.id !== id)
        },
        addTodo(todo){
          this.todos.push(todo)
        }
    }
    
  }
  </script>
  
  <style scoped>
    select {
        padding: 10px;
        border-radius: 8px;
        font-size: 16px;
    }
  </style>