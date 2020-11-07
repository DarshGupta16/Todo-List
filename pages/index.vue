<template>
  <div>
    <h1>My Todos</h1>
    <form @submit.prevent="onSubmit" style="padding-bottom: 10px">
      <input v-model="todoInput" type="text" class="input" />
      <input type="submit" value="Add Todo" class="btn" />
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
  width: 23%;
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
