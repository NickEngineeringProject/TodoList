<template>
    <div>
        <h2>Todo application</h2>
        <todo-input @pushTodoItem="pushTodoItem"/>
        <todo-item v-for="(todo, i) of todos"
                   :index="i" :todo="todo"
                   @remove="removeTodo"
        />
    </div>
</template>

<script>
import TodoItem from "@/components/Todo/TodoItem";
import TodoInput from "@/components/Todo/TodoInput";
export default {
    name: "TodoList",
    props: {
      todos: Array
    },
    methods: {
        removeTodo (id) {
            this.$emit('remove', id)
        },
        pushTodoItem (todo) {
            this.$emit('push', todo)
        }
    },
    components: {TodoItem, TodoInput}
}
</script>

<style>

</style>