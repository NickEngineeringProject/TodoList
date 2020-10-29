<template>
    <div>
        <loading v-if="loading"/>
        <todo-list :todos="todos"
                   @remove="removeItem"
                   @push="pushItem"
                   v-else-if="todos.length"
        />
        <div v-else>Записей нет</div>
    </div>
</template>

<script>
import Loading from "@/components/Loading";
import TodoList from "@/components/Todo/TodoList";
import TodoInput from "@/components/Todo/TodoInput";
export default {
    name: "index",
    data () {
        return {
            todos: [],
            loading: true
        }
    },
    mounted() {
        fetch('https://jsonplaceholder.typicode.com/todos?_limit=5')
            .then(response => response.json())
            .then(json => {
                setTimeout(() => {
                    this.todos = json
                    this.loading = false
                }, 1000)
            }
            )
    },
    methods: {
        removeItem(id) {
            this.todos = this.todos.filter(T => T.id !== id)
        },
        pushItem(todo) {
            this.todos.push(todo)
        }
    },
    components: {TodoList, Loading, TodoInput}
}
</script>

<style>

</style>