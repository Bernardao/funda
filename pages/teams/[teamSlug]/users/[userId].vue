<template>
  <div>
    <p>{{ message }}</p>
  </div>
</template>

<script setup lang="ts">
const route = useRoute();
const message = computed(
  () => `I am on team ${route.params.teamSlug} and my user id is
    ${route.params.userId}`
);
</script>

<style scoped></style>
