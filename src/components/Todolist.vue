<template>
    <div id="">
        <ul>
            <TodoItem 
                v-for="(item, index) in todos" :key="item.title"
                v-bind:todo="item"
                v-bind:ind="index"
                v-on:remove="removeTodo"
            />
        </ul>
    </div>
</template>

<script>
import TodoItem from './TodoItem'
export default {
    props: ['todos'],
    components: {
        TodoItem
    },
    methods: {
        removeTodo(id){
            this.$emit('remove', id)
        }
    }
}
</script>

<style scoped>
    ul {
        list-style: none;
        margin: 0;
        padding: 0;
    }
</style>