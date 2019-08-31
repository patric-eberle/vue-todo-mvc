<template>
  <footer class="footer">
    <span class="todo-count">{{ amountOfItems }} items left</span>
    <ul class="filters">
      <li>
        <a href="#" @click="filter">All</a>
      </li>
      <li>
        <a href="#" @click="filter('active')">Active</a>
      </li>
      <li>
        <a href="#" @click="filter('completed')">Completed</a>
      </li>
    </ul>
    <button class="clear-completed" @click="$emit('clearCompleted')">Clear completed</button>
  </footer>
</template>

<script>
export default {
  name: "TodoListFooter",
  props: ["amountOfItems"],
  methods: {
    /**
     * Callback for the click event of a filter entry.
     */
    filter: function(type) {
      // Sends a "filter" event to the parent. The second argument is the data (payload), that will be sended with the event.
      this.$emit("filter", { filter: type });
    }
  }
};
</script>

<style scoped>
</style>


