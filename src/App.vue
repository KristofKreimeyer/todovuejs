<template>
  <div id="app" class="container col-6">
    <TodoList></TodoList>
  </div>
</template>

<script>
import TodoList from "./components/TodoList";

export default {
  name: 'App',
  components: {
    TodoList
  }
}
</script>

<style>
  @import "https://cdnjs.cloudflare.com/ajax/libs/animate.css/4.1.0/animate.min.css";
  @import "https://stackpath.bootstrapcdn.com/bootstrap/4.5.0/css/bootstrap.min.css";

  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }
</style>
