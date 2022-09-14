<template>
  <button @click="onClick()" class="btn" :style="{ background: color }">
    {{ text }}
  </button>
</template>

<script>
export default {
  name: "AddTaskButton",
  props: {
    text: String,
    color: String,
  },
  methods: {
    onClick() {
      this.$emit("button-click");
    },
  },
};
</script>
