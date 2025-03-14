<script setup lang="ts">
// Você pode escolher isso com base em uma chamada de API ou status de login
const layout = "default";
</script>

<template>
  <NuxtLayout :name="layout">
    <NuxtRouteAnnouncer />
    <NuxtPage />
  </NuxtLayout>
</template>