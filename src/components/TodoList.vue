<template>
  <div class="row">
    <div class="col-sm">
      <div class="mx-auto todo-list-content">
        <ul class="todo-list">
          <slot></slot>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "TodoList"
};
</script>
