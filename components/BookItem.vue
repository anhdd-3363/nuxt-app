<script setup>
import { formatPrice } from "@/utils/function.js";
defineProps(["book"]);
</script>

<template>
  <div
    class="bg-white border border-gray-200 rounded-lg hover:shadow-lg transition-shadow"
  >
    <NuxtLink :to="{ path: `/books/${book.id}` }">
      <div>
        <img
          class="object-cover w-full h-96 rounded-t-lg"
          :src="book.image"
          alt="product image"
        />
      </div>
    </NuxtLink>
    <div class="p-5">
      <NuxtLink :to="{ path: `/books/${book.id}` }">
        <h5
          class="text-lg tracking-tight text-gray-900 truncate hover:text-red-600 transtion-colors duration-150"
        >
          {{ book.name }}
        </h5>
      </NuxtLink>
      <div class="flex items-center justify-between">
        <span class="text-xl font-bold text-red-700">{{
          formatPrice(book.price)
        }}</span>
      </div>
    </div>
  </div>
</template>
