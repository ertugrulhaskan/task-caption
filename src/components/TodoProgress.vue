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
      let monthNames = [
        "January",
        "February",
        "March",
        "April",
        "May",
        "June",
        "July",
        "August",
        "September",
        "October",
        "November",
        "December"
      ];
      let dayNames = [
        "Sunday",
        "Monday",
        "Tuesday",
        "Wednesday",
        "Thursday",
        "Friday",
        "Saturday"
      ];
      let date = new Date();
      return `${date.getDate()} ${
        monthNames[date.getMonth()]
      } ${date.getFullYear()}, ${dayNames[date.getDay()]}`;
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
