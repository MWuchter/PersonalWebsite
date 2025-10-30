<template>
  <header class="bg-white border-b border-gray-200 sticky top-0 z-50 shadow-sm">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="flex justify-between items-center h-16">
        <router-link to="/" class="text-2xl font-bold text-primary-600 hover:text-primary-700 transition-colors">
          Maxwell Wuchter
        </router-link>
        <nav class="flex gap-8">
          <router-link 
            to="/projects" 
            class="text-gray-600 hover:text-primary-600 transition-colors font-medium"
            active-class="text-primary-600 border-b-2 border-primary-600"
          >
            Projects
          </router-link>
          <router-link 
            to="/skills" 
            class="text-gray-600 hover:text-primary-600 transition-colors font-medium"
            active-class="text-primary-600 border-b-2 border-primary-600"
          >
            Skills
          </router-link>
          <router-link 
            to="/education" 
            class="text-gray-600 hover:text-primary-600 transition-colors font-medium"
            active-class="text-primary-600 border-b-2 border-primary-600"
          >
            Education
          </router-link>
        </nav>
      </div>
    </div>
  </header>
</template>

<script setup>
// Navigation header
</script>
