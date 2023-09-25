<script setup>
import { useAuthStore } from "@/stores/auth";
import { computed } from "vue";

const handleLogout = () => {
  window.location.href = "/";
};
const authStore = useAuthStore();
const isLogin = computed(() => authStore.getUser);
</script>

<template>
  <nav class="max-w-screen-xl mx-auto">
    <div
      class="max-w-screen-xl flex flex-wrap items-center justify-between mx-auto py-4 h-20"
    >
      <NuxtLink to="/" class="flex items-center">
        <img
          src="@/assets/img/nuxt.png"
          class="h-8 mr-3 inline-block"
          alt="Bookshop Logo"
        />

        <span class="self-center text-2xl font-semibold whitespace-nowrap"
          >Bookshop</span
        >
      </NuxtLink>
      <SearchItem />
      <ul class="font-medium flex flex-row">
        <template v-if="isLogin">
          <li>
            <NuxtLink
              to="/profile"
              class="py-2 pl-4 text-black flex items-center"
              aria-current="page"
            >
              <IconProfile />
              <span>
                {{ isLogin.name }}
              </span>
            </NuxtLink>
          </li>
          <li>
            <NuxtLink
              to="/cart"
              class="py-2 pl-4 text-black flex items-center"
              aria-current="page"
            >
              <IconCart />
              <span> Giỏ hàng </span>
            </NuxtLink>
          </li>
          <li
            @click="handleLogout"
            class="cursor-pointer py-2 pl-4 text-black flex items-center"
          >
            <IconLogout />
            <span>Đăng xuất</span>
          </li>
        </template>
        <template v-else>
          <li>
            <NuxtLink
              to="/login"
              class="py-2 pl-4 text-black flex items-center"
              aria-current="page"
            >
              <IconLogin />
              <span> Đăng nhập </span>
            </NuxtLink>
          </li>
          <li>
            <NuxtLink
              to="/register"
              class="py-2 pl-4 text-black flex items-center"
              aria-current="page"
            >
              <IconRegister />
              <span> Đăng ký </span>
            </NuxtLink>
          </li>
          <li>
            <NuxtLink
              to="/cart"
              class="py-2 pl-4 text-black flex items-center"
              aria-current="page"
            >
              <IconCart />
              <span> Giỏ hàng</span>
            </NuxtLink>
          </li>
        </template>
      </ul>
    </div>
  </nav>
</template>
