<template>
  <div>
    <h1>Done Todos</h1>
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

<script>
export default {
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
