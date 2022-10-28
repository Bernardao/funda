<template>
  <div>Estoy en admin</div>
</template>

<script setup lang="ts">
definePageMeta({
  middleware: ['auth'],
})
</script>

<style scoped></style>
