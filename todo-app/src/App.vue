<template>
  <div>
    <img src="./assets/logo.png">
    <todo-list v-bind:todos="todos"></todo-list>
    <create-todo v-on:create-todo="addTodo"></create-todo>
  </div>
</template>


<script>
import TodoList from './components/TodoList';
import CreateTodo from './components/CreateTodo';

export default {
  name: 'App',
  components: {
    TodoList,
    CreateTodo,
  },

  methods: {
    addTodo(todo) {
      this.todos.push({
        title: todo.title,
        project: todo.project,
        isDone: todo.isDone,
      });
    },
  },

  data() {
    return {
      todos: [{
        id: 0,
        title: 'Todo A',
        project: 'Project A',
        isDone: false,
      }, {
        id: 1,
        title: 'Todo B',
        project: 'Project B',
        isDone: true,
      }, {
        id: 2,
        title: 'Todo C',
        project: 'Project C',
        isDone: false,
      }, {
        id: 3,
        title: 'Todo D',
        project: 'Project D',
        isDone: false,
      }],
    };
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
