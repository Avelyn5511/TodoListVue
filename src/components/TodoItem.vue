<template>
  <li class="todo-item">
    <span
      class="todo-text"
      :class="{ completed: todo.completed }"
      @click="toggleComplete"
    >
      {{ todo.text }}
    </span>
    <button @click="removeTodo">Удалить</button>
  </li>
</template>

<script>
export default {
  name: "TodoItem",
  props: {
    todo: {
      type: Object,
      required: true,
    },
  },
  methods: {
    removeTodo() {
      this.$emit("remove-todo", this.todo.id);
    },
    toggleComplete() {
      this.$emit("toggle-complete", this.todo.id);
    },
  },
};
</script>

<style scoped>
.todo-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 10px;
  border: 1px solid #ddd;
  margin-bottom: 5px;
  border-radius: 4px;
}
.todo-text {
  cursor: pointer;
}
.todo-text.completed {
  text-decoration: line-through;
  color: gray;
}
button {
  background-color: #ff4d4d;
  color: white;
  border: none;
  padding: 5px 10px;
  border-radius: 4px;
  cursor: pointer;
}
button:hover {
  background-color: #ff1a1a;
}
</style>
