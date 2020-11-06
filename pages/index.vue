<template>
  <div>
    <h1>My Todos</h1>
  </div>
</template>

<script lang="ts">
export default {
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
