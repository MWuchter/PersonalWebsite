<template>
  <div class="min-h-screen flex flex-col">
    <Header />
    <main class="flex-1">
      <router-view />
    </main>
    <footer class="bg-gray-900 text-gray-300 py-8 mt-16">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 text-center">
        <p>&copy; 2025 Max Wuchter. All rights reserved.</p>
      </div>
    </footer>
  </div>
</template>

<script setup>
import Header from './components/Header.vue'
</script>
