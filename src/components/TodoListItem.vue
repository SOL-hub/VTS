<template>
  <li>
    <span class="item-wrap" @click="toggleItem" :class="todoItemClass">{{
      todoItem.title
    }}</span>
    <!-- <button @click="$emit('delete')">삭제</button> -->
    <button @click="removeItem">삭제</button>
  </li>
</template>

<script lang="ts">
import Vue from "vue";
import { PropType } from "vue/types/v3-component-props";
import { Todo } from "../App.vue";

export default Vue.extend({
  props: {
    todoItem: Object as PropType<Todo>,
    index: Number,
  },

  computed: {
    todoItemClass(): string | null {
      return this.todoItem.done ? "complete" : null;
    },
  },

  methods: {
    toggleItem() {
      this.$emit("toggle", this.todoItem, this.index);
    },
    removeItem() {
      this.$emit("remove", this.index);
    },
  },
});
</script>

<style scoped>
.item-wrap {
  cursor: pointer;
}
.complete {
  text-decoration: line-through;
}
</style>
