<template>
  <div class="todo">
    <p>完了済タスク: {{todos.filter(todo => {return todo.done === true}).length}}</p>
    <p>未完了タスク: {{todos.filter(todo => {return todo.done === false}).length}}</p>
    <todo-card v-for="todo in todos" v-bind:todo="todo" @delete-todo="deleteTodo" @complete-todo="completeTodo"></todo-card>
  </div>
</template>
<script type = "text/javascript" >
import TodoCard from './TodoCard';
export default {
  props: ['todos'],
  components: {
    TodoCard
  },
  methods: {
    deleteTodo(todo) {
      const todoIndex = this.todos.indexOf(todo);
      this.todos.splice(todoIndex, 1);
    },
    completeTodo(todo) {
      const todoIndex = this.todos.indexOf(todo);
      this.todos[todoIndex].done = !this.todos[todoIndex].done;
    },
  },
};
</script>
<style>
</style>