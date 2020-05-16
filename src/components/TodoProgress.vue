<template>
  <div class="row">
    <div class="col-sm">
      <div class="todo-progress-box">
        <div class="d-flex align-items-center justify-content-between">
          <h3>{{ this.getToday }}</h3>
          <small>{{ this.getDone }} / {{ this.getTodosCount }}</small>
        </div>
        <div class="progress-todo">
          <div class="progress-completed" :style="{ width: `${rate}%` }"></div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import moment from "moment";

export default {
  name: "TodoProgress",
  props: {
    todosListing: Array
  },
  data: function() {
    return {};
  },
  mounted: function() {},
  computed: {
    getToday: function() {
      return moment(new Date()).format("MMMM Do YYYY, dddd");
    },
    getTodosCount: function() {
      return this.todosListing.length;
    },
    getDone: function() {
      return this.todosListing.filter(item => item.completed === true).length;
    },
    rate: function() {
      return parseInt((this.getDone / this.getTodosCount) * 100, 10);
    }
  }
};
</script>

<style lang="scss" scoped></style>
