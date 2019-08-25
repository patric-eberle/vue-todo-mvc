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
        @keyup.enter="addTodo"
      >
    </header>
    <section class="main">
      <input id="toggle-all" class="toggle-all" type="checkbox" v-model="allDone">
      <label for="toggle-all"></label>
      <ul class="todo-list">
        <li
          v-for="(todo, index) in todos"
          :key="index"
          class="todo"
          :class="{ completed: todo.isDone }"
        >
          <div class="view">
            <input class="toggle" type="checkbox" v-model="todo.isDone">
            <label>{{ todo.text }}</label>
            <button class="destroy" @click="removeTodo(todo)"></button>
          </div>
        </li>
      </ul>
    </section>
    <TodoListFooter :amountOfItems="remaining"/>
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
  },
  computed: {
    /**
     * Counts the amount of todos which are not done yet.
     */
    remaining: function() {
      // Filters todos by their isDone state and counts the length of items that are not done yet
      return this.todos.filter(function(todo) {
        return todo.isDone !== true;
      }).length;
    },

    /**
     * Gets/sets the isDone value of all todo items in the list.
     */
    allDone: {
      // Method which is called when the current value is requested
      get: function() {
        return this.remaining === 0;
      },
      // Method which is called when the value should be changed
      set: function(value) {
        this.todos.forEach(function(todo) {
          todo.isDone = value;
        });
      }
    }
  },
  methods: {
    /**
     * Adds a new item to the list of todos with the newTodo value as it's text.
     */
    addTodo: function() {
      const text = this.newTodo && this.newTodo.trim();

      // Check if a todo text is available
      if (!text) {
        return;
      }

      // Extend todo list
      this.todos.push({
        text: text,
        isDone: false
      });

      // Reset input value
      this.newTodo = "";
    },

    /**
     * Remove the given todo.
     */
    removeTodo(todo) {
      // Searches for the given todo inside the todo list and deletes it (splices out)
      this.todos.splice(this.todos.indexOf(todo), 1);
    }
  }
};
</script>

<style scoped>
</style>
