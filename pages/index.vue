<template>
  <div>
    <h1>My Todos</h1>
    <form style="padding-bottom: 10px" @submit.prevent="onSubmit">
      <input v-model="todoInput" type="text" class="input" />
      <button type="submit" class="btn">Add Todo</button>
    </form>
    <div v-if="todos.length != 0" class="todo-container">
      <div v-for="(todo, index) in todos" :key="index" class="todo-box">
        <div class="title-container">
          <h1 style="font-size: 20px">{{ todo }}</h1>
        </div>
        <div class="options">
          <button class="btn-options" @click="addDoneTodos(index)">
            <i class="fas fa-check"></i>
          </button>
          <button class="btn-options" @click="editTodo(index)">
            <i class="far fa-edit"></i>
          </button>
          <button class="btn-options" @click="deleteTodo(index)">
            <i class="fas fa-trash"></i>
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<style>
@import url('https://fonts.googleapis.com/css2?family=Montserrat&display=swap');
@import url('https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.1/css/all.min.css');

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
  font-size: 20px;
  border: none;
  border-radius: none;
  outline: none;
  font-family: 'Montserrat', sans-serif;
  cursor: pointer;
}

.todo-box {
  display: flex;
  align-items: center;
  text-align: center;
  justify-content: space-around;
  padding-bottom: 10px;
}

.title-container {
  width: 5%;
}
</style>

<script>
export default {
  data() {
    return {
      todos: [],
      doneTodos: [],
      todoInput: '',
    }
  },
  mounted() {
    this.todos = JSON.parse(localStorage.getItem('todos')) || []
    this.doneTodos = JSON.parse(localStorage.getItem('doneTodos')) || []
  },
  methods: {
    onSubmit() {
      this.todos.push(this.todoInput)
      localStorage.setItem('todos', JSON.stringify(this.todos))
      this.todoInput = ''
    },
    addDoneTodos(index) {
      this.doneTodos.push(this.todos.splice(index, 1))
      localStorage.setItem('doneTodos', JSON.stringify(this.doneTodos))
    },
    editTodo(index) {
      this.todoInput = this.todos.splice(index, 1)
    },
    deleteTodo(index) {
      this.todos.splice(index, 1)
      localStorage.setItem('todos', JSON.stringify(this.todos))
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
