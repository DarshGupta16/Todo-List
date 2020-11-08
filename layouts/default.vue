<template>
  <div>
    <NavBar />
    <Nuxt />
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

<style>
@import url('https://fonts.googleapis.com/css2?family=Montserrat&display=swap');
@import url('https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.1/css/all.min.css');
@import url('https://cdnjs.cloudflare.com/ajax/libs/animate.css/4.1.1/animate.compat.css');

html {
  font-family: 'Montserrat', sans-serif;
  font-size: 16px;
  word-spacing: 1px;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  box-sizing: border-box;
  text-align: center;
}

*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
}

.button--green {
  display: inline-block;
  border-radius: 4px;
  border: 1px solid #3b8070;
  color: #3b8070;
  text-decoration: none;
  padding: 10px 30px;
}

.button--green:hover {
  color: #fff;
  background-color: #3b8070;
}

.button--grey {
  display: inline-block;
  border-radius: 4px;
  border: 1px solid #35495e;
  color: #35495e;
  text-decoration: none;
  padding: 10px 30px;
  margin-left: 15px;
}

.button--grey:hover {
  color: #fff;
  background-color: #35495e;
}

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

.animated {
  animation-duration: 2s;
}
</style>
