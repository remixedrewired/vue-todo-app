<template>
  <div>
    <form @submit.prevent="onSubmit">
      <input type="text" v-model="title" name="title" placeholder="Add Todo...">
      <input type="submit" value="Submit" class="btn">
    </form>
  </div>
</template>

<script>
import { mapActions } from "vuex";
export default {
  name: "AddTodo",
  data() {
    return {
      title: ""
    };
  },
  methods: {
    ...mapActions(["addTodo"]),
    onSubmit() {
      this.addTodo(this.title);
      this.title = "";
    }
  }
};
</script>

<style scoped>
form {
  display: flex;
  padding-top: 20px;
}
input[type="text"] {
  flex: 10;
  padding: 5px;
  margin-right: 10px;
  border-radius: 5px;
  border-style: dotted;
  border-color: #555555;
}
input[type="submit"] {
  flex: 2;
  border-radius: 5px;
}
</style>
