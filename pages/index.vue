<template>
  <div>
    <h1>My Todos</h1>
    <form @submit.prevent="onSubmit">
      <input v-model="todoInput" type="text" />
      <input type="submit" value="Add Todo" />
    </form>
  </div>
</template>

<script lang="ts">
export default {
  data() {
    return {
      todos: ['My Todo List', 'Always remember to finish all your work'],
      todoInput: '',
    }
  },
  mounted() {
    this.todos = JSON.parse(localStorage.getItem('todos')!)
  },
  methods: {
    onSubmit() {
      this.todos.push(this.todoInput)
      localStorage.setItem('todos', JSON.stringify(this.todos))
      this.todoInput = ''
    },
  },
  head() {
    return {
      title: 'My Todos',
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: 'Create your own goals and todos and accomplish them! :D',
        },
      ],
    }
  },
}
</script>

<style lang="scss" scoped></style>
