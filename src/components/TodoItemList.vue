<script setup lang="ts">
import type { Todo } from '@/types/todo.ts';
import TodoItem from './TodoItem.vue';

// Here, we define input props of type `Todo[]`.
const props = defineProps<{
    todos: Todo[],
}>()

// Here, we define the custom event `clicked` that we will emit with id of clicked todo.
// We do this, so that the `App` component will now which exact todo was clicked.
const emits = defineEmits<{
    clicked: [id: number],
}>()

const onClick = (id: number) => {
    emits('clicked', id);
}

</script>

<template>
    <!-- Similar to our App component, we pass the todo object as a prop. -->
    <TodoItem
        v-for="todo in todos"
        :key="todo.id"
        :todo 
        @clicked="onClick"/>
</template>