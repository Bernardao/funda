<script setup lang="ts">
// const isLoggedIn = useIsLoggedIn()
const user = useUser()
definePageMeta({
  layout: 'plain',
})
</script>
<template>
  <div>
    <form @submit.prevent="user.login" class="login-form">
      <h1>Login</h1>
      <label>
        Username
        <input type="text" />
      </label>
      <label>
        Password
        <input type="password" />
      </label>
      <button>Login</button>
    </form>
  </div>
</template>

<style scoped></style>
