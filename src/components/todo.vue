<template>
  <header class="flex justify-between px-5 bg-gray-300 w-100">
    <Icons />
    <h1 class="text-left relative top-1">Список задач</h1>
    <a @click="del" href="#!" title="Удалить">
      <svg class="icon w-8 h-8">
        <use xlink:href="#delete"></use>
      </svg>
    </a>
  </header>
  <div class="container min-h-100 flex-grow py-4">
    <ul class="flex flex-col items-center">
      <Task
        v-for="(task, idx) in tasks"
        :key="idx.trim()"
        :taskText="task"
        :tasks="tasks"
        :idx="idx"
        @toggleCheck="changedKey"
      />
    </ul>
  </div>
  <form
    v-on:submit.prevent="addTask"
    action=""
    class="form flex justify-evenly mb-10"
  >
    <button type="submit">
      <svg class="icon w-6 h-6">
        <use xlink:href="#plus"></use>
      </svg>
    </button>
    <input
      @keydown.enter="handleSubmit"
      v-model="inputTask"
      type="text"
      class="border border-gray-300 rounded-md w-4/5"
      minlength="3"
      maxlength="60"
      placeholder="Работа не волк"
    />
  </form>
</template>

<script>
import Icons from "./parts/icons";
import Task from "./parts/task";

export default {
  name: "Todo",
  components: {
    Icons,
    Task,
  },
  data() {
    return {
      inputTask: "",
      tasks: {},
      currentTask: "",
      checkedTaskIds: [],
    };
  },

  methods: {
    addTask: function () {
      if (this.inputTask.trim() !== '')
        this.tasks[
          this.inputTask.slice(-4, -1) + this.inputTask.slice(0, 3)
        ] = this.inputTask;
      return (this.inputTask = "");
    },

    changedKey(key) {
      if (key[1]) {
        this.currentTask = key[0];
        this.checkedTaskIds.push(this.currentTask);
      } else {
        this.currentTask = "";
        this.checkedTaskIds.splice(this.checkedTaskIds.indexOf(key[0]), 1);
      }
    },

    del() {
      this.checkedTaskIds.map((item) =>
        item !== this.tasks[item] ? delete this.tasks[item] : item
      );
      return this.checkedTaskIds = []
    },
  },

  computed: {},

  watch: {},
};
</script>

<style>
</style>

// refs
{
  /* <svg class="icon">
  <use xlink:href="#checkbox-blank-circle-outline"></use>
</svg><svg class="icon">
  <use xlink:href="#checkbox-marked-circle-outline"></use>
</svg><svg class="icon">
  <use xlink:href="#delete"></use>
</svg><svg class="icon">
  <use xlink:href="#plus"></use>
</svg><svg class="icon">
  <use xlink:href="#trash-can-outline"></use>
</svg> */
}