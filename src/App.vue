<template>
  <div id="app">
    <Header />
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" />
  </div>
</template>

<script>
import Todos from "./components/Todos";
import Header from './components/layout/Header';

export default {
  name: "App",
  components: {
    Todos,
    Header
  },
  methods: {
    deleteTodo: function(id) {
      this.todos = this.todos.filter(todo => todo.id !== id);
    }
  },
  data: function() {
    return {
      todos: [
        { id: 1, task: "Learn JavaScript ES6", done: true },
        { id: 2, task: "Learn React", done: false },
        { id: 3, task: "Learn Block-chain technology", done: true },
        { id: 4, task: "Attend a meet up", done: true }
      ]
    };
  }
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.4;
}
</style>
