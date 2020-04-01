<template>
  <div>
    <TodoForm @addTodo="addTodo" />
    <ul>
      <li v-for="todo in todos" :key="todo.id">
        <TodoItemComponent :text="todo.text" />
      </li>
    </ul>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import TodoItemComponent from "@/components/TodoItem.vue";
import TodoForm from "@/components/TodoForm.vue";

interface TodoItem {
  id?: number;
  text?: string;
  isDone?: boolean;
}

@Component({
  components: {
    TodoItemComponent,
    TodoForm,
  },
})
export default class Todo extends Vue {
  todos: Array<TodoItem> = [];
  currentID = 1;

  addTodo(text: string) {
    this.currentID += this.todos.length + 1;
    this.todos = [
      ...this.todos,
      { id: this.currentID, text: text, isDone: false },
    ];
  }
}
</script>
