<template>
  <div>
    <!-- Renders TodoList component -->
    <todo-list v-bind:todos="todos"></todo-list>
    <!-- Renders CreateTodo component -->
    <create-todo v-on:create-todo="createTodo"></create-todo>
  </div>
</template>

<script>
import TodoList from './components/TodoList';
import CreateTodo from './components/CreateTodo';

export default {
  name: 'app',
  components: {
    TodoList,
    CreateTodo,
  },
  data() {
    return {
      todos: [{
        title: 'Ready job search materials',
        project: 'Personal portfolio / Resume / LinkedIn / Clean-up GitHub',
        done: true,
      }, {
        title: 'Lightning Talk',
        project: 'Prep and present Vue.js',
        done: false,
      }, {
        title: 'WDI 39 Final Project',
        project: 'Plan / Develop / Present',
        done: false,
      }, {
        title: 'Business Cards',
        project: 'Buy through MOO or Zazzle',
        done: true,
      }],
    };
  },
  methods: {
    createTodo(newTodo) {
      this.todos.push(newTodo);
    },
  },
};
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
