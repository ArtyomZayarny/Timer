<template>
  <div id="app">
    <AddTimer
      @add-todo="addTodo"
    />
    <hr class="line">
    <TodoList
            v-bind:todos="todos"
            @remove-todo="removeTodo"
    />
  </div>
</template>

<script>
import TodoList from './components/TodoList'
import AddTimer from './components/AddTimer'
import Timer from './components/Timer'
export default {
  name: 'App',
  data() {
    return {
      todos: []
    }
  },
  components: {
    TodoList,AddTimer,Timer
  },
  methods: {
    removeTodo(id) {
      this.todos = this.todos.filter( todo => todo.id !== id);
    },
    addTodo(todo) {
      this.todos.unshift(todo)
    }
  }
}
</script>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Nunito+Sans:wght@300;400;800&display=swap');
  body {
    font-family: 'Nunito Sans', sans-serif;
  }
  hr {
    background: #E7E8EA;
  }
</style>
