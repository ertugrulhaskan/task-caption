<template>
  <div>
    <todo-header @todoAdding="addTodo"></todo-header>
    <div class="container">
      <todo-progress :todosListing="todos"></todo-progress>
      <todo-list>
        <todo-item
          v-for="todo in todos"
          :key="todo._id"
          :todo="todo"
          @todoUpdating="updateTodo"
          @todoRemoving="deleteTodo"
        ></todo-item>
      </todo-list>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src

import TodoHeader from "../components/TodoHeader";
import TodoProgress from "../components/TodoProgress";
import TodoList from "../components/TodoList";
import TodoItem from "../components/TodoItem";

export default {
  name: "Home",
  data() {
    return {
      todos: [
        {
          _id: 1578246344875,
          todoItem: "Learn VueJS",
          completed: true
        },
        {
          _id: 1578249168815,
          todoItem: "Learn ReactJS",
          completed: false
        },
        {
          _id: 1578249181270,
          todoItem: "Learn Meteor",
          completed: true
        },
        {
          _id: 1578249181288,
          todoItem: "Meet your friends",
          completed: false
        }
      ]
    };
  },
  components: {
    TodoHeader,
    TodoList,
    TodoItem,
    TodoProgress
  },
  methods: {
    addTodo: function(newTodoItem) {
      this.todos.push(newTodoItem);
    },
    updateTodo: function() {
      this.todos.push();
    },
    deleteTodo: function(todoID) {
      let fetchIndex = this.todos
        .map(item => item._id === todoID)
        .indexOf(true);
      this.todos.splice(fetchIndex, 1);
    }
  }
};
</script>
