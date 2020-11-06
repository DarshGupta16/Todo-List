<template>
  <div>
    <h1>Done Todos</h1>
  </div>
</template>

<script lang="ts">
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
