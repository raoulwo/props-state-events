<script setup lang="ts">
import type { Todo } from '@/types/todo.ts';
import TodoItem from './TodoItem.vue';

const props = defineProps<{
    todos: Todo[],
}>()

const emits = defineEmits<{
    clicked: [id: number],
}>()

const onClick = (id: number) => {
    emits('clicked', id);
}

</script>

<template>
    <TodoItem
        v-for="todo in todos"
        :key="todo.id"
        :todo 
        @clicked="onClick"/>
</template>