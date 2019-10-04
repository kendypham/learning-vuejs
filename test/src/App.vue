<template>
  <div id="app">
    <Todos v-bind:todos='todos'/>
  </div>
</template>

<script>
import Todos from "./components/Todos.vue";

export default {
  name: "app",
  components: {
    Todos
  },
  data() {
    return {
      todos: [
        {
          id: 1,
          title: 'Todo one',
          completed: false,
        },
        {
          id: 2,
          title: 'Todo two',
          completed: true,
        },
        {
          id: 3,
          title: 'Todo three',
          completed: false,
        },
      ]
    };
  }
};
</script>

<style>
</style>
