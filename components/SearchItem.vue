<script setup>
import { ref } from "vue";
import { useRouter } from "vue-router";

const router = useRouter();
const textSearch = ref("");

const handleSearch = function () {
  router.push({ name: "search", query: { q: textSearch.value } });
};
</script>

<template>
  <div class="relative w-96">
    <div
      class="absolute inset-y-0 left-0 flex items-center pl-3 pointer-events-none"
    >
      <IconSearch />
    </div>
    <BaseInput
      type="text"
      placeholder="Tìm kiếm"
      class="pl-10 pr-24"
      v-model.trim="textSearch"
      @input="handleSearch"
    />
  </div>
</template>
