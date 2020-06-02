<template>
  <div class="todo-item" v-bind:class="{'is-completed': todo.done}">
    <ul>
      <li>
        <input type="checkbox" v-on:change="markCompleted" />
        {{ todo.task}}
        <button @click="$emit('del-todo', todo.id)" class="del">X</button>
      </li>
    </ul>
  </div>
</template>
<script>
export default {
  name: "TodoItem",
  props: ["todo"],

  methods: {
    markCompleted: function() {
      this.todo.done = !this.todo.done;
    }
  }
};
</script>

<style scoped>
.todo-item {
  background: #f4f4f4;
  padding: 10px;
  border-bottom: 1px #ccc dotted;
}
.is-completed {
  text-decoration: line-through;
}
.del {
  background: #ff0000;
  color: #fff;
  border: none;
  padding: 5px 9px;
  border-radius: 50%;
  cursor: pointer;
  float: right;
}
</style>