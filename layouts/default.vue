<script setup lang="ts">
const user = useUser()
</script>
<template>
  <div class="main-layout">
    <nav class="main-nav">
      <NuxtLink to="/">Home</NuxtLink>
      <NuxtLink to="/movies">Movies</NuxtLink>
      <NuxtLink to="https://vueschool.io">Vue School</NuxtLink>
      <NuxtLink v-if="!user.isLoggedIn" to="/login">Login</NuxtLink>
      <a href="#" v-else @click.prevent="user.isLoggedIn = false" to="/login"
        >Logout</a
      >
    </nav>
    <slot></slot>
  </div>
</template>

<style scoped>
.main-nav {
  display: flex;
  gap: 10px;
}
</style>
