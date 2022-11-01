<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
    <h1>Todo application</h1>
    <AddTodo
      @add-todo="addTodo"
    />
    <hr>
    <TodoList
      v-bind:todos="todos"
      @rm-todo="rmTodo"
    />
  </div>
</template>

<script>
import TodoList from '@/components/TodoList.vue'
import AddTodo from '@/components/AddTodo.vue'

export default {
  name: 'App',
  data() {
    return {
      todos: [
        // {id: 1, title: 'Купить хлеб', completed: false},
        // {id: 2, title: 'Купить молоко', completed: false},
        // {id: 3, title: 'Покормить кошку', completed: false},
      ]
    }
  },
  mounted () {
    fetch('https://jsonplaceholder.typicode.com/todos?_limit=5')
      .then(response => response.json())
      .then(json => {
        this.todos = json
      })
  },
  components: {
    TodoList, AddTodo
  },
  methods: {
    rmTodo (id) {
      this.todos = this.todos.filter(t => t.id !== id);
    },
    addTodo (todo) {
      this.todos.push(todo);
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
