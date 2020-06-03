<template>
    <div>
   <ul>
       <TodoItem
           v-for="(todo, i) of todos"
           v-bind:todo="todo"
           v-bind:index="i"
           v-on:remove-todo="removeTodo"
       />
   </ul>
    </div>
</template>


<script>
    import TodoItem  from '../components/TodoItem'
    export default {
        props:['todos'],
        components: {
            TodoItem
        },
        methods: {
            removeTodo(id) {
                this.$emit('remove-todo',id)
            }
        }
    }
</script>

<style scoped>
    ul {
        list-style: none;
        max-width: 485px;
        margin: 0 auto;
    }
    li {
        display: flex;
        width: 100%;
        align-items: center;
        justify-content: flex-start;
        margin: 0 auto;
        padding-bottom: 40px;

    }
</style>