    // @change="$emit('check', [idx, checked])"
<template>
  <li
    @click="toggleCheck(), $emit('toggleCheck', [idx, checked])"
    @onDblClick.prevent
    class="w-3/4 relative flex items-center cursor-pointer"
  >
    <picture>
      <img
        v-show="!checked"
        class="relative min-w-min"
        width="22"
        height="22"
        src="../../assets/img-todo/checkbox-blank-circle-outline.svg"
        alt="blank"
      />
      <img
        v-show="checked"
        class="relative min-w-min"
        width="22"
        height="22"
        src="../../assets/img-todo/checkbox-marked-circle-outline.svg"
        alt="marked"
      />
    </picture>
    <span class="relative px-4 my-2 select-none">{{ taskText }}</span>
  </li>
</template>

<script>
export default {
  name: "Task",

  props: {
    tasks: Object,
    taskText: String,
    idx: String,
  },

  data() {
    return {
      checked: false,
    };
  },

  methods: {
    toggleCheck() {
      return (this.checked = !this.checked);
    },
  },
};
</script>