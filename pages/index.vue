<template>
  <div>
    <h1>My Todos</h1>
    <form @submit.prevent="onSubmit">
      <input v-model="todoInput" type="text" class="input" />
      <input type="submit" value="Add Todo" class="btn" />
    </form>
  </div>
</template>

<style>
@import url('https://fonts.googleapis.com/css2?family=Montserrat&display=swap');

.input {
  font-size: 30px;
  border: 1px solid black;
  border-radius: none;
  outline: none;
  width: 500px;
}

.btn {
  font-size: 30px;
  border: none;
  border-radius: none;
  outline: none;
  background-color: #52de97;
  font-family: 'Montserrat', sans-serif;
  cursor: pointer;
}
</style>

<script lang="ts">
export default {
  data() {
    type todos = object[]
    return {
      todos: [],
      todoInput: '',
    }
  },
  mounted() {
    this.todos = JSON.parse(localStorage.getItem('todos')!) || []
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
