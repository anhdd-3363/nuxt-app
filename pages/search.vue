<script setup>
import { getBooksByKeywordApi } from "@/apis/book";
import { onMounted, ref, watch } from "vue";

const route = useRoute();
const books = ref([]);

const handleSearch = async () => {
  if (!route.query.q) books.value = [];
  else
    try {
      const { data } = await getBooksByKeywordApi(route.query.q);
      books.value = data;
    } catch (error) {
      // handle error
    }
};

watch(() => route.query.q, handleSearch);

onMounted(handleSearch);
</script>

<template>
  <div class="my-12">
    <p v-if="route.query.q" class="text-3xl">
      Kết quả: Có {{ books.length }} sản phẩm chứa từ khóa "{{ route.query.q }}"
    </p>
    <p v-else class="text-3xl">Hãy nhập từ khóa để tìm kiếm</p>
    <BookList :list="books" />
  </div>
</template>
