<template>
  <div class="navbar">
    <nuxt-link to="/" class="link">
      <h1>Real World Events</h1>
    </nuxt-link>
    <div class="right">
      <nuxt-link to="/" class="link">My Todos</nuxt-link> &nbsp; |
      <nuxt-link to="/done-todos" class="link">Done Todos</nuxt-link>
    </div>
  </div>
</template>

<style>
.navbar {
  display: flex;
  align-items: center;
  justify-content: space-around;
}

.link {
  text-decoration: none;
  color: #52de97;
}

.link:hover {
  text-decoration: underline;
}
</style>
