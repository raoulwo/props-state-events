<script setup lang="ts">
import type { Todo } from '@/types/todo.ts';

// Here, we define input props of type `Todo`.
const props = defineProps<{
    todo: Todo;
}>()

// Here, we define the custom event `clicked` that we will emit with id of clicked todo.
const emits = defineEmits<{
    clicked: [id: number],
}>()
</script>

<template>
    <div @click="emits('clicked', todo.id)">
        <p :class="{ done: todo.done }">{{ todo.text }}</p>
    </div>
</template>

<style scoped>
    p {
        cursor: pointer;
        font-size: 2rem;
    }

    .done {
    text-decoration: line-through;
    color: #888; /* Optional: fade it out a bit */
    }
</style>
