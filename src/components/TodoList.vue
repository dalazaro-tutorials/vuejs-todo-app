<!-- This component holds a compiled list of todos from the hard-coded data from App.vue -->
<template>
  <div>
    <!-- JavaScript expressions in Vue are enclosed in double curly brackets. -->
    <div style="text-align:center;font-weight:700;">
      <p>Completed Tasks: {{todos.filter(todo => {return todo.done === true}).length}}</p>
      <p>Pending Tasks: {{todos.filter(todo => {return todo.done === false}).length}}</p>
    </div>

    <!-- invoking the todo component -->
    <todo
      v-on:delete-todo="deleteTodo"
      v-on:complete-todo="completeTodo"
      v-on:pending-todo="pendingTodo"
      v-for="todo in todos"
      :todo.sync="todo"
    >
    </todo>
  </div>
</template>

<script>
import Todo from './Todo';

export default {
  props: ['todos'],
  components: {
    Todo,
  },
  methods: {
    deleteTodo(todo) {
      const todoIndex = this.todos.indexOf(todo);
      this.todos.splice(todoIndex, 1);
    },
    completeTodo(todo) {
      const todoIndex = this.todos.indexOf(todo);
      this.todos[todoIndex].done = true;
    },
    pendingTodo(todo) {
      const todoIndex = this.todos.indexOf(todo);
      this.todos[todoIndex].done = false;
    },
  },
};
</script>
