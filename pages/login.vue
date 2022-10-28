<script setup lang="ts">
const isLoggedIn = useIsLoggedIn()
definePageMeta({
  layout: 'plain',
})
function login() {
  isLoggedIn.value = true
  useRouter().push('/')
}
</script>
<template>
  <div>
    <form @submit.prevent="login" class="login-form">
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
