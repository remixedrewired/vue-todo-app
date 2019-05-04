<template>
  <div>
    <h1>Todos</h1>
    <div class="legend">
      <span>Double click to mark as complete</span>
      <span>
        <span class="incomplete-box"></span> = Incomplete
      </span>
      <span>
        <span class="complete-box"></span> = Complete
      </span>
    </div>
    <div class="todos">
      <TodoItem
        v-for="todo in allTodos"
        v-bind:todo="todo"
        :key="todo.id"
        v-bind:class="{'is-complete': todo.completed}"
      />
    </div>
  </div>
</template>
<script>
import TodoItem from "./TodoItem.vue";
import { mapGetters, mapActions } from "vuex";

export default {
  name: "Todos",
  components: {
    TodoItem
  },
  methods: mapActions(["fetchTodos"]),
  computed: mapGetters(["allTodos"]),
  created() {
    this.fetchTodos();
  }
};
</script>
<style scoped>
.todos {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-gap: 1rem;
}

.legend {
  display: flex;
  justify-content: space-around;
  margin-bottom: 1rem;
}
.complete-box {
  display: inline-block;
  width: 10px;
  height: 10px;
  background: #35495e;
}
.incomplete-box {
  display: inline-block;
  width: 10px;
  height: 10px;
  background: #41b883;
}
.is-complete {
  background: #35495e;
  color: #fff;
}
@media (max-width: 500px) {
  .todos {
    grid-template-columns: 1fr;
  }
}
</style>
