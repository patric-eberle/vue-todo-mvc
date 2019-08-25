<template>
  <footer class="footer">
    <span class="todo-count">{{ amountOfItems }} items left</span>
    <ul class="filters">
      <li>
        <a href="#/all">All</a>
      </li>
      <li>
        <a href="#/active">Active</a>
      </li>
      <li>
        <a href="#/completed">Completed</a>
      </li>
    </ul>
    <button class="clear-completed">Clear completed</button>
  </footer>
</template>

<script>
export default {
  name: "TodoListFooter",
  props: ["amountOfItems"]
};
</script>

<style scoped>
</style>


