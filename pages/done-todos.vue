<template>
  <div>
    <h1>Done Todos</h1>
    <div v-if="doneTodos.length != 0" class="todo-container">
      <div v-for="(todo, index) in doneTodos" :key="index" class="todo-box">
        <div class="title-container">
          <h1 style="font-size: 20px">{{ todo }}</h1>
        </div>
        <div class="options">
          <button class="btn-options" @click="restoreTodo(index)">
            <i class="fas fa-undo"></i>
          </button>
          <button class="btn-options" @click="deleteTodo(index)">
            <i class="fas fa-trash"></i>
          </button>
        </div>
      </div>
      <button class="btn-options" @click="deleteAllTodos">
        Delete all Todos
      </button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      todos: [],
      doneTodos: [],
    }
  },
  mounted() {
    this.todos = JSON.parse(localStorage.getItem('todos')) || []
    this.doneTodos = JSON.parse(localStorage.getItem('doneTodos')) || []
  },
  methods: {
    restoreTodo(index) {
      const item = this.doneTodos.splice(index, 1)
      item.forEach((i) => {
        this.todos.push(i)
      })
      localStorage.setItem('todos', JSON.stringify(this.todos))
      localStorage.setItem('doneTodos', JSON.stringify(this.doneTodos))
    },
    async deleteTodo(index) {
      const confirmation = await prompt(
        'Are you sure you want to delete this? Warning: This action is irreversible! Write Yes or No',
        'Yes'
      )
      if (confirmation.toLowerCase() === 'yes') {
        this.doneTodos.splice(index, 1)
        localStorage.setItem('doneTodos', JSON.stringify(this.doneTodos))
      } else if (confirmation.toLowerCase() === 'no') {
      } else {
        alert('Value entered is invalid.')
      }
    },
    async deleteAllTodos() {
      const confirmation = await prompt(
        'Are you sure you want to delete all done todos? Warning: this action is irreverible! Write Yes or No',
        'Yes'
      )
      if (confirmation.toLowerCase() === 'yes') {
        this.doneTodos = []
        localStorage.setItem('doneTodos', JSON.stringify(this.todos))
      } else if (confirmation.toLowerCase() === 'no') {
      } else {
        alert('Value entered is invalid.')
      }
    },
  },
  head() {
    return {
      title: 'Done Todos',
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: 'All the todos you have done.',
        },
      ],
    }
  },
}
</script>
