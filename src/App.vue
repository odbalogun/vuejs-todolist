<template>
  <div>
    <todo-list v-bind:todos="todos"></todo-list>
    <create-todo v-on:add-todo="addTodo"></create-todo>
  </div>
</template>

<script>
import TodoList from './components/TodoList'
import CreateTodo from './components/CreateTodo'
import sweetalert from 'sweetalert'

export default {
  name: 'App',
  components: {
    TodoList,
    CreateTodo
  },
  methods: {
    createTodo (newTodo) {
      this.todos.push(newTodo)
      sweetalert('Success!', 'To-Do created!', 'success')
    }
  },
  data () {
    return {
      todos: [
        {
          title: 'Todo A',
          project: 'Project A',
          done: true
        },
        {
          title: 'Todo B',
          project: 'Project B',
          done: false
        },
        {
          title: 'Todo C',
          project: 'Project C',
          done: true
        },
        {
          title: 'Todo D',
          project: 'Project D',
          done: false
        }
      ]
    }
  }
}
</script>

<style>

</style>
