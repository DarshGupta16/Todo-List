<template>
  <div>
    <h1>My Todos</h1>
    <form style="padding-bottom: 10px" @submit.prevent="onSubmit">
      <input v-model="todoInput" type="text" class="input" />
      <button type="submit" class="btn">Add Todo</button>
    </form>
    <div v-if="todos.length != 0" class="todo-container">
      <transition-group name="fadeInUp">
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
      </transition-group>
      <button class="btn-options" @click="deleteAllTodos">
        Delete all Todos
      </button>
    </div>
  </div>
</template>

<style>
@keyframes fade {
  0% {
    transform: rotate(0) translateX(-100px);
    opacity: 0;
  }
  12% {
    transform: rotate(0) translateX(-80px);
    opacity: 0.2;
  }
  25% {
    transform: rotate(0) translateX(-60px);
    opacity: 0.4;
  }
  41% {
    transform: rotate(0) translateX(-40px);
    opacity: 0.6;
  }
  63% {
    transform: rotate(0) translateX(-20px);
    opacity: 0.8;
  }
  85% {
    transform: rotate(0) translateX(0px);
    opacity: 0.9;
  }
  100% {
    transform: rotate(0) translateX(0px);
    opacity: 1;
  }
}

.elementToAnimate {
  animation: yourAnimation 1s 1 0s linear;
}
</style>

<script>
export default {
  transition: 'fade',
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
      const item = this.todos.splice(index, 1)
      item.forEach((i) => {
        this.doneTodos.push(i)
      })
      localStorage.setItem('todos', JSON.stringify(this.todos))
      localStorage.setItem('doneTodos', JSON.stringify(this.doneTodos))
    },
    editTodo(index) {
      this.todoInput = this.todos.splice(index, 1)
    },
    async deleteTodo(index) {
      const confirmation = await prompt(
        'Are you sure you want to delete this todo? Warning: this action is irreverible! Write Yes or No',
        'Yes'
      )
      if (confirmation.toLowerCase() === 'yes') {
        this.todos.splice(index, 1)
        localStorage.setItem('todos', JSON.stringify(this.todos))
      } else if (confirmation.toLowerCase() === 'no') {
      } else {
        alert('Value entered is invalid.')
      }
    },
    async deleteAllTodos() {
      const confirmation = await prompt(
        'Are you sure you want to delete all todos? Warning: this action is irreverible! Write Yes or No',
        'Yes'
      )
      if (confirmation.toLowerCase() === 'yes') {
        this.todos = []
        localStorage.setItem('todos', JSON.stringify(this.todos))
      } else if (confirmation.toLowerCase() === 'no') {
      } else {
        alert('Value entered is invalid.')
      }
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
