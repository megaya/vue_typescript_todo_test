<template>
  <form @submit.prevent="addTodo">
    <input type="text" v-model="text" />
    <button type="submit">追加</button>
  </form>
</template>

<script lang="ts">
import { Component, Vue, Emit } from "vue-property-decorator";

@Component
export default class TodoItem extends Vue {
  text = "";

  @Emit("addTodo")
  emitAddTodo(text: string): string {
    return text;
  }

  addTodo() {
    this.emitAddTodo(this.text);
    this.text = "";
  }

}
</script>
