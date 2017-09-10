<!-- This component gets rendered inside the div#app in index.html. -->
<template>
  <div>
    <!-- invokes TodoList component -->
    <todo-list v-bind:todos="todos"></todo-list>
    <!-- invokes CreateTodo component -->
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
  // hard-coded starter data
  data() {
    return {
      todos: [{
        title: 'Ready job search materials',
        description: 'Personal portfolio / Resume / LinkedIn / Clean-up GitHub',
        done: true,
      }, {
        title: 'Lightning Talk',
        description: 'Prep and present Vue.js',
        done: false,
      }, {
        title: 'WDI 39 Final Project',
        description: 'Plan / Develop / Present',
        done: false,
      }, {
        title: 'Business Cards',
        description: 'Buy through MOO or Zazzle',
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
