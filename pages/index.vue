<template>
  <div>
    <h1>My Todos</h1>
    <form @submit.prevent="onSubmit">
      <input v-model="todoInput" type="text" class="input" />
      <input type="submit" value="Add Todo" class="btn" />
    </form>
    <div class="todo-container" v-if="todos.length != 0">
      <div class="todo-box" v-for="(todo, index) in todos" :key="index">
        <h1>{{ todo }}</h1>
        <div class="options">
          <button class="btn-options" @click="addDoneTodos(index)">
            Add to Done Todos
          </button>
          <button class="btn-options" @click="editTodo(index)">
            Edit Todo
          </button>
          <button class="btn-options" @click="deleteTodo(index)">
            Delete Todo
          </button>
        </div>
      </div>
    </div>
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

.btn-options {
  background-color: #eee;
  font-size: 30px;
  border: none;
  border-radius: none;
  outline: none;
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
