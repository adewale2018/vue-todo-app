<template>
  <div>
    <form @submit="addTodo">
      <input
        type="text"
        placeholder="Add todo..."
        name="title"
        v-model="title"
        required
      />
      <input type="submit" value="Submit" class="btn" />
    </form>
  </div>
</template>

<script>
// import { v4 as uuidv4 } from "uuid";

export default {
  name: "AddTodo",
  data: function() {
    return {
      title: "",
    };
  },
  methods: {
    addTodo: function(e) {
      e.preventDefault();
      if (this.title.length !== 0 && this.title.trim() !== "") {
        const newTodo = {
          title: this.title,
          completed: false,
        };
        //send up to the parent
        this.$emit("add-todo", newTodo);
        this.title = "";
      }
    },
  },
};
</script>

<style scoped>
form {
  display: flex;
}
input[type="text"] {
  flex: 10;
  padding: 5px;
}
input[type="submit"] {
  flex: 2;
}
</style>
