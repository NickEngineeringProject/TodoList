<template>
    <div>
        <form @submit.prevent="handler(index)">
            <label>
                <input type="text" v-model="title">
            </label>
            <button type="submit">submit</button>
        </form>
    </div>
</template>

<script>
export default {
    name: "TodoInput",
    props: {
        index: Number
    },
    data () {
        return {
            title: ''
        }
    },
    methods: {
        handler(index) {
            if (this.title.trim()) {
                const todo = {
                    id: index,
                    title: this.title,
                    completed: false
                }
                this.$emit('pushTodoItem', todo)
                this.title = ''
            }
        }
    }
}
</script>

<style scoped>

</style>