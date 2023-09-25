<template>
  <header>
    <NavBar />
  </header>
  <div class="max-w-screen-xl min-h-screen mx-auto">
    <slot></slot>
  </div>
  <footer class="w-full border-t-2">
    <BaseFooter />
  </footer>
</template>
