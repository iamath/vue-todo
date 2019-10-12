<template>
  <div class="container pt-5">
    <Form @submited="addTodo" />
    <ul class="list-group mt-3">
      <Todo
        v-for="(todo, i) in todos"
        :key="i"
        :task="{ name: todo.name, completed: todo.completed, i }"
        @removed="removeTodo(i)"
        @completed="completeTodo(i)"
      />
    </ul>
  </div>
</template>

<script>
import Form from './Form'
import Todo from './Todo'

export default {
  components: {
    Form,
    Todo
  },
  data() {
    return {
      todos: []
    }
  },
  methods: {
    changeTodo() {
      const completed = this.todos.filter((todo) => { return todo.completed })
      const uncompleted = this.todos.filter((todo) => { return !todo.completed })

      this.todos = [...uncompleted, ...completed]
    },
    addTodo(name) {
      if (name !== '') {
        this.todos.unshift({ name, completed: false })
        this.changeTodo()
      }
    },
    removeTodo(i) {
      this.todos.splice(i, 1)
      this.changeTodo()
    },
    completeTodo(i) {
      this.todos[i].completed = true
      this.changeTodo()
    }
  }
}
</script>
