<template>
  <nav class="bg-purple-600 text-white">
    <div class="container mx-auto">
      <div class="flex items-center">
        <router-link
          class="inline-block px-16 py-4 transition-colors hover:bg-purple-500 duration-300"
          :to="{ name: 'Home' }"
          >Home</router-link
        >
        <router-link
          class="inline-block px-16 py-4 transition-colors hover:bg-purple-500 duration-300"
          :to="{ name: 'Todos' }"
          >Todos</router-link
        >
      </div>
    </div>
  </nav>
  <router-view />
</template>

<style>
body {
  background-color: #eeeeff;
}
</style>
