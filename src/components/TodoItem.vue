<template>
    <li>
        <span v-bind:class="{done: todo.completed}">
            <input type="checkbox" 
            v-on:change="todo.completed = !todo.completed">
            <strong>{{ind+1}}</strong>
            {{todo.title | uppercase}}
        </span>
        <button class="rm" type="submit"
        v-on:click="$emit('remove', todo.id)"
        >&times;
        </button>
    </li>
</template>

<script>
export default {
    props: {
        todo: {
            type: Object,
            required: true
        },
        ind: Number
    },
    filters: {
        uppercase(value) {
            console.log(value)
            return value.toUpperCase()
        }
    }
}
</script>

<style scoped>
    li {
        border: 1px solid gray;
        display: flex;
        justify-content: space-between;
        padding: 2px;
        margin-bottom: 5px;
    }

    .rm{
        background-color: red;
        color: black;
        border-radius: 5px;
    }

    .done {
        text-decoration: line-through;
    }
</style>