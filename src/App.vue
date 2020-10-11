<template>
  <div id="app">
    <h1>Todo app</h1>
    <AddTodo v-on:add-todo="AddNewTodo" />
    <select v-model="filter">
      <option value="all">All</option>
      <option value="completed">Comleted</option>
      <option value="not-completed">Not completed</option>
    </select>
    <hr />
    <TodoList v-bind:todos="filterTodos" v-on:remove="removeTodo" />
  </div>
</template>

<script>
import TodoList from "@/components/Todolist";
import AddTodo from "@/components/AddTodo";
export default {
  name: "App",
  data() {
    return {
      todos: [
        { id: 1, title: "buy bread", completed: false },
        { id: 2, title: "buy milk", completed: false },
        { id: 3, title: "buy shuger", completed: false },
      ],
      filter: "all",
    };
  },
  methods: {
    removeTodo(id) {
      this.todos = this.todos.filter((t) => t.id != id);
    },
    AddNewTodo(todo) {
      this.todos.push(todo);
    },
  },
  components: {
    TodoList,
    AddTodo,
  },
  /*   watch: {
    filter(value) {
      console.log(value)
    }
  } */
  computed: {
    filterTodos() {
      if (this.filter === "all") {
        return this.todos;
      }
      if (this.filter === "completed") {
        return this.todos.filter((t) => t.completed);
      }
      if (this.filter === "not-completed") {
        return this.todos.filter((t) => !t.completed);
      }
    },
  },
};
</script>


<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
