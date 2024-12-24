<template>
  <div>
    <form class="form-container" @submit.prevent="addTodo">
      <input v-model="newTodo" placeholder="Введите задачу" />
      <button type="submit" class="add">Добавить</button>
    </form>
    <ul class="todo-list">
      <todo-item
        v-for="todo in todos"
        :key="todo.id"
        :todo="todo"
        @remove-todo="removeTodo"
        @toggle-complete="toggleComplete"
      />
    </ul>
  </div>
</template>

<script>
import TodoItem from "./TodoItem.vue";

export default {
  name: "TodoList",
  components: {
    TodoItem,
  },
  data() {
    return {
      newTodo: "",
      todos: [],
    };
  },
  methods: {
    addTodo() {
      if (this.newTodo.trim() === "") return;
      const newTask = {
        id: Date.now(),
        text: this.newTodo.trim(),
        completed: false,
      };
      this.todos.push(newTask);
      this.newTodo = "";
    },
    removeTodo(id) {
      this.todos = this.todos.filter((todo) => todo.id !== id);
    },
    toggleComplete(id) {
      const todo = this.todos.find((todo) => todo.id === id);
      if (todo) todo.completed = !todo.completed;
    },
  },
};
</script>

<style scoped>
.form-container {
  display: flex;
  margin-bottom: 20px;
}
input {
  flex: 1;
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 4px;
  margin-right: 10px;
}
button.add {
  background-color: #4caf50;
  color: white;
  border: none;
  padding: 5px 10px;
  border-radius: 4px;
  cursor: pointer;
}
button.add:hover {
  background-color: #45a049;
}
.todo-list {
  list-style-type: none;
  padding: 0;
}
</style>
