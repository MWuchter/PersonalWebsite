<template>
  <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8 py-12">
    <div v-if="project">
      <!-- Back Button -->
      <router-link 
        to="/projects" 
        class="inline-flex items-center text-primary-600 hover:text-primary-700 font-medium mb-8 transition-colors group"
      >
        <svg class="w-5 h-5 mr-2 transform group-hover:-translate-x-1 transition-transform" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7"></path>
        </svg>
        Back to Projects
      </router-link>

      <!-- Project Header -->
      <div class="mb-12">
        <div class="flex flex-wrap items-center gap-4 mb-4">
          <span class="px-4 py-1 bg-primary-100 text-primary-700 text-sm font-semibold rounded-full">
            {{ project.status }}
          </span>
          <span class="text-gray-500">{{ project.timeline }}</span>
        </div>
        <h1 class="text-4xl md:text-5xl font-bold text-gray-900 mb-4">{{ project.title }}</h1>
        <p class="text-xl text-gray-600 mb-6">{{ project.description }}</p>
        
        <!-- Action Buttons -->
        <div class="flex flex-wrap gap-4">
          <a 
            v-if="project.githubUrl" 
            :href="project.githubUrl" 
            target="_blank" 
            rel="noopener noreferrer"
            class="inline-flex items-center px-6 py-3 bg-gray-900 text-white rounded-lg font-semibold hover:bg-gray-800 transition-colors shadow-md"
          >
            <svg class="w-5 h-5 mr-2" fill="currentColor" viewBox="0 0 24 24">
              <path d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/>
            </svg>
            View on GitHub
          </a>
          <a 
            v-if="project.liveUrl" 
            :href="project.liveUrl" 
            target="_blank" 
            rel="noopener noreferrer"
            class="inline-flex items-center px-6 py-3 bg-primary-600 text-white rounded-lg font-semibold hover:bg-primary-700 transition-colors shadow-md"
          >
            <svg class="w-5 h-5 mr-2" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10 6H6a2 2 0 00-2 2v10a2 2 0 002 2h10a2 2 0 002-2v-4M14 4h6m0 0v6m0-6L10 14"></path>
            </svg>
            View Live Demo
          </a>
        </div>

        <!-- Tags -->
        <div class="flex flex-wrap gap-2 mt-6">
          <span 
            v-for="tag in project.tags" 
            :key="tag" 
            class="px-4 py-2 bg-gray-100 text-gray-700 text-sm font-medium rounded-lg hover:bg-gray-200 transition-colors"
          >
            {{ tag }}
          </span>
        </div>
      </div>

      <!-- Project Content Grid -->
      <div class="grid lg:grid-cols-3 gap-8">
        <!-- Main Content (2/3) -->
        <div class="lg:col-span-2 space-y-8">
          <!-- Overview -->
          <section class="bg-white rounded-2xl shadow-sm border border-gray-200 p-8">
            <h2 class="text-2xl font-bold text-gray-900 mb-4 flex items-center">
              <svg class="w-6 h-6 mr-2 text-primary-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 16h-1v-4h-1m1-4h.01M21 12a9 9 0 11-18 0 9 9 0 0118 0z"></path>
              </svg>
              Project Overview
            </h2>
            <p class="text-gray-700 text-lg leading-relaxed">{{ project.detailedDescription || project.description }}</p>
          </section>

          <!-- Key Features -->
          <section class="bg-white rounded-2xl shadow-sm border border-gray-200 p-8">
            <h2 class="text-2xl font-bold text-gray-900 mb-6 flex items-center">
              <svg class="w-6 h-6 mr-2 text-primary-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7"></path>
              </svg>
              Key Features
            </h2>
            <ul class="space-y-3">
              <li 
                v-for="(feature, index) in project.features" 
                :key="index"
                class="flex items-start group"
              >
                <svg class="w-5 h-5 text-primary-600 mr-3 mt-0.5 flex-shrink-0" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z"></path>
                </svg>
                <span class="text-gray-700 group-hover:text-gray-900 transition-colors">{{ feature }}</span>
              </li>
            </ul>
          </section>

          <!-- Technologies Deep Dive -->
          <section class="bg-white rounded-2xl shadow-sm border border-gray-200 p-8">
            <h2 class="text-2xl font-bold text-gray-900 mb-6 flex items-center">
              <svg class="w-6 h-6 mr-2 text-primary-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10 20l4-16m4 4l4 4-4 4M6 16l-4-4 4-4"></path>
              </svg>
              Technologies Used
            </h2>
            <div class="grid grid-cols-2 md:grid-cols-3 gap-4">
              <div 
                v-for="tech in project.technologies" 
                :key="tech"
                class="bg-gradient-to-br from-primary-50 to-white border border-primary-200 rounded-lg p-4 text-center font-medium text-gray-800 hover:shadow-md transition-all hover:scale-105"
              >
                {{ tech }}
              </div>
            </div>
          </section>
        </div>

        <!-- Sidebar (1/3) -->
        <div class="space-y-6">
          <!-- Project Info Card -->
          <div class="bg-gradient-to-br from-gray-50 to-white rounded-2xl shadow-sm border border-gray-200 p-6 sticky top-20">
            <h3 class="text-lg font-bold text-gray-900 mb-4">Project Information</h3>
            <div class="space-y-4">
              <div>
                <p class="text-sm text-gray-500 mb-1">Role</p>
                <p class="font-semibold text-gray-900">{{ project.role }}</p>
              </div>
              <div>
                <p class="text-sm text-gray-500 mb-1">Timeline</p>
                <p class="font-semibold text-gray-900">{{ project.timeline }}</p>
              </div>
              <div>
                <p class="text-sm text-gray-500 mb-1">Status</p>
                <span 
                  class="inline-block px-3 py-1 text-sm font-semibold rounded-full"
                  :class="{
                    'bg-green-100 text-green-700': project.status === 'Completed' || project.status === 'Active' || project.status === 'Deployed',
                    'bg-yellow-100 text-yellow-700': project.status === 'In Development' || project.status === 'Ongoing',
                    'bg-orange-100 text-orange-700': project.status === 'Incomplete/Development'
                  }"
                >
                  {{ project.status }}
                </span>
              </div>
              <div v-if="project.technologies && project.technologies.length > 0">
                <p class="text-sm text-gray-500 mb-2">Tech Stack</p>
                <div class="flex flex-wrap gap-2">
                  <span 
                    v-for="tech in project.technologies.slice(0, 5)" 
                    :key="tech"
                    class="px-2 py-1 bg-primary-100 text-primary-700 text-xs font-medium rounded"
                  >
                    {{ tech }}
                  </span>
                </div>
              </div>
            </div>

            <!-- Links Section -->
            <div class="mt-6 pt-6 border-t border-gray-200 space-y-3">
              <a 
                v-if="project.githubUrl" 
                :href="project.githubUrl" 
                target="_blank" 
                rel="noopener noreferrer"
                class="flex items-center text-gray-700 hover:text-primary-600 transition-colors group"
              >
                <svg class="w-5 h-5 mr-2 group-hover:scale-110 transition-transform" fill="currentColor" viewBox="0 0 24 24">
                  <path d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/>
                </svg>
                GitHub Repository
              </a>
              <a 
                v-if="project.liveUrl" 
                :href="project.liveUrl" 
                target="_blank" 
                rel="noopener noreferrer"
                class="flex items-center text-gray-700 hover:text-primary-600 transition-colors group"
              >
                <svg class="w-5 h-5 mr-2 group-hover:scale-110 transition-transform" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 12a9 9 0 01-9 9m9-9a9 9 0 00-9-9m9 9H3m9 9a9 9 0 01-9-9m9 9c1.657 0 3-4.03 3-9s-1.343-9-3-9m0 18c-1.657 0-3-4.03-3-9s1.343-9 3-9m-9 9a9 9 0 019-9"></path>
                </svg>
                Live Demo
              </a>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- Not Found -->
    <div v-else class="text-center py-20">
      <div class="mb-8">
        <svg class="w-24 h-24 text-gray-400 mx-auto" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9.172 16.172a4 4 0 015.656 0M9 10h.01M15 10h.01M21 12a9 9 0 11-18 0 9 9 0 0118 0z"></path>
        </svg>
      </div>
      <h1 class="text-4xl font-bold text-gray-900 mb-4">Project Not Found</h1>
      <p class="text-gray-600 mb-8">Sorry, we couldn't find the project you're looking for.</p>
      <router-link 
        to="/projects" 
        class="inline-flex items-center px-6 py-3 bg-primary-600 text-white rounded-lg font-semibold hover:bg-primary-700 transition-colors"
      >
        <svg class="w-5 h-5 mr-2" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7"></path>
        </svg>
        Back to Projects
      </router-link>
    </div>
  </div>
</template>

<script setup>
import { computed } from 'vue'
import { useRoute } from 'vue-router'
import projects from '../data/projects.json'

const route = useRoute()
const project = computed(() => {
  const id = parseInt(route.params.id)
  return projects.find(p => p.id === id)
})
</script>
