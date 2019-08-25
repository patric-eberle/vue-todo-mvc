<template>
  <section class="todoapp">
    <header class="header">
      <h1>{{ title }}</h1>
      <input
        class="new-todo"
        autofocus
        autocomplete="off"
        placeholder="What needs to be done?"
        v-model="newTodo"
      >
    </header>
    <section class="main">
      <input id="toggle-all" class="toggle-all" type="checkbox">
      <label for="toggle-all"></label>
      <ul class="todo-list">
        <li v-for="(todo, index) in todos" :key="index" class="todo">
          <div class="view">
            <input class="toggle" type="checkbox">
            <label>{{ todo.text }}</label>
            <button class="destroy"></button>
          </div>
        </li>
      </ul>
    </section>
    <TodoListFooter/>
  </section>
</template>

<script>
import TodoListFooter from "./TodoListFooter.vue";

export default {
  name: "TodoList",
  components: {
    TodoListFooter: TodoListFooter
  },
  data() {
    return {
      title: "todos",
      newTodo: "",
      todos: [
        { text: "Learn JavaScript ES6+ goodies", isDone: true },
        { text: "Learn Vue", isDone: false },
        { text: "Build something awesome", isDone: false }
      ]
    };
  }
};
</script>

<style scoped>
</style>
