<template>
  <div class="container">
    <h1>My Todos</h1>
    <div id="app">
      <TodoBoard :todos="todos" @addTodo="addTodo" @deleteTodo="deleteTodo" @changeStatusTodo="changeStatusTodo" />
    </div>
  </div>
</template>

<script>
import TodoBoard from './components/TodoBoardview.vue';

export default {
  data() {
    return {
      todos: [],
    };
  },
  methods: {
    addTodo(newTodo) {
      this.todos.push(newTodo);
    },
    deleteTodo(todoId) {
      this.todos = this.todos.filter(todo => todo.id !== todoId);
    },
    changeStatusTodo(todoId) {
      this.todos = this.todos.map(todo => {
        if (todo.id === todoId) {
          todo.completed = !todo.completed;
        }
        return todo;
      });
    },
  },
  components: {
    TodoBoard,
  },
};
</script>

<style>
#app {
  text-align: center;
  display: flex;
  justify-content: center;
}
.container {
  display: block;
  background-color: whitesmoke;
  width: 1000px;
  height: 300px;
  box-shadow: transparent;
}
</style>