<template>
  <div>
    <NavBar />
    <transition name="page">
      <Nuxt />
    </transition>
  </div>
</template>

<script lang="ts">
import NavBar from '@/components/NavBar.vue'
export default {
  components: {
    NavBar,
  },
  head() {
    return {
      titleTemplate: '%s - Real World Todos',
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
