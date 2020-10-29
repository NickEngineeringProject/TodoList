<template>
    <div>
        <label :class="{done: todo.completed}">
            <input type="checkbox"
                   @change="todo.completed = !todo.completed">
            <span>{{index + 1}}</span>
            <strong>{{todo.title}}</strong>
        </label>
        <button @click="$emit('remove', todo.id)">
            &times
        </button>
    </div>
</template>

<script>
export default {
    name: "TodoItem",
    props: {
        todo: Object,
        index: Number
    },
}
</script>

<style>
    .done {
        text-decoration: line-through;
    }
</style>