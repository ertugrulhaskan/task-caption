<template>
  <li>
    <input type="checkbox" :checked="todo.completed" :id="todo._id" />
    <label :for="todo._id" @click.prevent="todoState(todo)">
      {{ todo.todoItem }}
    </label>
    <button type="button" @click.prevent="todoRemove(todo._id)">-</button>
  </li>
</template>

<script>
export default {
  name: "TodoItem",
  props: {
    todo: Object
  },
  data: function() {
    return {};
  },
  mounted: function() {},
  methods: {
    todoState: function(todo) {
      this.$set(todo, "completed", !todo.completed);
      this.$emit("todoUpdating");
    },
    todoRemove: function(todoID) {
      this.$emit("todoRemoving", todoID);
    }
  }
};
</script>
