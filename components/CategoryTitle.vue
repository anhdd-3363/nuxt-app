<script setup>
defineProps(["title", "id"]);
</script>

<template>
  <div class="text-center my-4">
    <NuxtLink
      :to="{ path: `/collections/${id}` }"
      class="text-2xl font-bold text-gray-900"
    >
      {{ title }}
    </NuxtLink>
  </div>
  <hr class="h-px my-4 bg-gray-200 border-0" />
</template>
