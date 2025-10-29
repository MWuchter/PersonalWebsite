<template>
  <router-link 
    v-if="isInternal" 
    :to="link"
    class="block"
  >
    <article class="bg-white rounded-lg border border-gray-200 p-6 hover:shadow-lg hover:border-primary-300 transition-all duration-300 hover:-translate-y-1 cursor-pointer group">
      <h3 class="text-xl font-bold mb-3 text-gray-900 group-hover:text-primary-600 transition-colors">
        {{ title }}
      </h3>
      <p class="text-gray-600 mb-4 line-clamp-3">{{ description }}</p>
      <div class="flex flex-wrap gap-2">
        <span 
          v-for="tag in tags" 
          :key="tag" 
          class="px-3 py-1 bg-primary-50 text-primary-700 text-sm font-medium rounded-full"
        >
          {{ tag }}
        </span>
      </div>
    </article>
  </router-link>
  <a 
    v-else 
    :href="link" 
    target="_blank" 
    rel="noopener noreferrer"
    class="block"
  >
    <article class="bg-white rounded-lg border border-gray-200 p-6 hover:shadow-lg hover:border-primary-300 transition-all duration-300 hover:-translate-y-1 cursor-pointer group">
      <h3 class="text-xl font-bold mb-3 text-gray-900 group-hover:text-primary-600 transition-colors">
        {{ title }}
      </h3>
      <p class="text-gray-600 mb-4 line-clamp-3">{{ description }}</p>
      <div class="flex flex-wrap gap-2">
        <span 
          v-for="tag in tags" 
          :key="tag" 
          class="px-3 py-1 bg-primary-50 text-primary-700 text-sm font-medium rounded-full"
        >
          {{ tag }}
        </span>
      </div>
    </article>
  </a>
</template>

<script setup>
defineProps({
  title: String,
  description: String,
  link: { type: String, default: '#' },
  tags: { type: Array, default: () => [] },
  isInternal: { type: Boolean, default: false }
})
</script>
