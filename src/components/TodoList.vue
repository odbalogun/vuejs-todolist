<template>
  <div>
    <p class="tasks">Completed Tasks: {{ todos.filter(todo => { return todo.done === true}).length }}</p>
    <p class="tasks">Pending Tasks: {{ todos.filter(todo => { return todo.done === false}).length }}</p>
    <todo v-on:delete-todo="deleteTodo" v-on:complete-todo="completeTodo" v-for="todo in todos" :todo.sync="todo" :key="todo"></todo>
  </div>
</template>

<script type="text/javascript">
import Todo from './Todo'
import sweetalert from 'sweetalert'

export default {
  props: ['todos'],
  components: {
    Todo
  },
  methods: {
    deleteTodo (todo) {
      sweetalert({
        title: 'Are you sure?',
        text: 'This To-Do will be permanently deleted!',
        type: 'warning',
        showCancelButton: true,
        confirmButtonColor: '#DD6B55',
        confirmButtonText: 'Yes, delete it!',
        closeOnConfirm: false
      }).then(() => {
        const todoIndex = this.todos.indexOf(todo)
        this.todos.splice(todoIndex, 1)
        sweetalert('Deleted!', 'Your To-Do has been deleted.', 'success')
      })
    },
    completeTodo (todo) {
      const todoIndex = this.todos.indexOf(todo)
      this.todos[todoIndex].done = true
      sweetalert('Success!', 'To-Do completed!', 'success')
    }
  }
}
</script>

<style scoped>
p.tasks {
  text-align: center;
}
</style>
