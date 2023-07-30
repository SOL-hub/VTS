<template>
  <div>
    <label for="todo-input"></label>
    <input id="todo-input" type="text" :value="item" @input="handleInput" />
    <button type="button" @click="addTodo">add</button>
  </div>
</template>

<script lang="ts">
import Vue from "vue";

export default Vue.extend({
  props: ["item"], //item이라는 프롭스 속성을 받을 준비
  methods: {
    handleInput(event: any) {
      event.target.value;
      this.$emit("input", event.target.value);
    },
    addTodo() {
      console.log("add");
    },
  },
});
</script>

<style scoped></style>
