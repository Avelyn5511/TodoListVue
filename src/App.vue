<template>
  <div class="todo-container">
    <h1>Список дел</h1>
    <todo-list />
  </div>
</template>

<script>
import TodoList from "./components/TodoList.vue";

export default {
  name: "App",
  components: {
    TodoList,
  },
};
</script>

<style>
body {
  font-family: Arial, sans-serif;
  margin: 20px;
}
.todo-container {
  max-width: 500px;
  margin: auto;
  text-align: center;
}
h1 {
  color: #4caf50;
}
</style>
