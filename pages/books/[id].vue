<script setup>
import { getDetailBookApi } from "@/apis/book";
import { ref, onMounted } from "vue";

const route = useRoute();
const id = route.params.id;
const bookDetail = ref({});
const getBookDetailData = async () => {
  try {
    const { data } = await getDetailBookApi(id);
    bookDetail.value = data;
  } catch (error) {
    // handle error
  }
};
onMounted(getBookDetailData);
</script>

<template>
  <ProductDetail :product-detail="bookDetail" />
</template>
