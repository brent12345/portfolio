<script setup>
//  const layout = 'another'
</script>
  

<template>

  <div>
  <NuxtLayout>
    <NuxtPage />
  </NuxtLayout>
  </div>
</template>

<style>
.layout-enter-active,
.layout-leave-active {
  transition: all 0.1s;
}
.layout-enter-from,
.layout-leave-to {
  filter: blur(1);
  opacity: 0;
}
</style>
