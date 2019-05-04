<template>
  <div class="todo" @dblclick="onDblClick(todo)">
    <p>
      {{todo.title}}
      <i @click="deleteTodo(todo.id)" class="fas fa-trash-alt"></i>
    </p>
  </div>
</template>
<script>
import { mapActions } from "vuex";

export default {
  name: "TodoItem",
  props: ["todo"],
  methods: {
    ...mapActions(["deleteTodo", "updateTodo"]),
    onDblClick(todo) {
      const updTodo = {
        ...todo,
        completed: !todo.completed
      };
      console.log("TCL: onDblClick -> updTodo", updTodo);
      this.updateTodo(updTodo);
    }
  }
};
</script>
<style scoped>
.todo {
  border: 1px solid #ccc;
  background: #41b883;
  padding: 1rem;
  border-radius: 5px;
  text-align: center;
  position: relative;
  cursor: pointer;
}
i {
  position: absolute;
  bottom: 10px;
  right: 10px;
  color: #fff;
  cursor: pointer;
}
</style>
