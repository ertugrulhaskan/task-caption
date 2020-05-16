<template>
  <header class="py-3 todo-header">
    <div class="container">
      <div class="row">
        <div class="col-sm">
          <h1>todo</h1>
          <form class="d-flex justify-content-center my-2 mx-auto form-control">
            <input
              type="text"
              name="todo"
              id="todo"
              maxlength="140"
              placeholder="Just do something..."
              v-model="todoItem"
            />
            <button @click.prevent="createTodo">+</button>
          </form>
        </div>
      </div>
    </div>
  </header>
</template>

<script>
export default {
  name: "TodoHeader",
  data: function() {
    return {
      todoItem: ""
    };
  },
  methods: {
    createTodo: function() {
      this.$emit("todoAdding", {
        _id: Date.parse(new Date()),
        todoItem: this.todoItem,
        completed: false
      });
      this.todoItem = "";
    }
  }
};
</script>

<style lang="scss"></style>
