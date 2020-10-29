<template>
    <div>
        <todo-list :todos="todos"
                   @remove="removeItem"
                   @push="pushItem"
        />
    </div>
</template>

<script>
import TodoList from "@/components/Todo/TodoList";
export default {
    name: "index",
    data () {
        return {
            todos: [
                {
                    id: 1,
                    title: 'title1',
                    description: 'description1',
                    completed: false
                },
                {
                    id: 2,
                    title: 'title2',
                    description: 'description12',
                    completed: false
                },
                {
                    id: 3,
                    title: 'title3',
                    description: 'description3',
                    completed: false
                },
            ]
        }
    },
    methods: {
        removeItem(id) {
            this.todos = this.todos.filter(T => T.id !== id)
        },
        pushItem(todo) {
            this.todos.push(todo)
        }
    },
    components: {TodoList},
}
</script>

<style>

</style>