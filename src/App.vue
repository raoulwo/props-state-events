<script setup lang="ts">
import { ref } from 'vue';
import TodoItemList from './components/TodoItemList.vue';
import type { Todo } from './types/todo.ts';

// Here, we have defined our *state* as a reactive variable.
const todos = ref<Todo[]>([
  {
    id: 1,
    text: 'Learn about props',
    done: true,
  },
  {
    id: 2,
    text: 'Learn about state',
    done: false,
  },
  {
    id: 3,
    text: 'Learn about events',
    done: false,
  }
])

const onClick = (id: number) => {
  const todo = todos.value.find(todo => todo.id === id);
  if (!todo) {
    return;
  }

  todo.done = !todo.done;
}
</script>

<template>
  <!-- Here, we pass down our reactive variable via prop. -->
  <!-- Here, we also listen for the custom `clicked` event. -->
  <TodoItemList :todos @clicked="onClick" />
</template>

<style scoped></style>
