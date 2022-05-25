<template>
  <div class="flex flex-col min-h-screen w-screen">
    <Todo />
  </div>
</template>

<script>
import Todo from "./components/todo.vue";

export default {
  name: "App",
  components: {
    Todo,
  },
};
</script>

<style>
</style>
