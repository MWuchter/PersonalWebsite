<template>
  <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-12">
    <!-- Hero Section -->
    <section class="text-center py-12 mb-12">
      <h1 class="text-5xl font-bold text-gray-900 mb-4">Education</h1>
      <p class="text-xl text-gray-600 max-w-2xl mx-auto">
        My academic journey and learning experiences
      </p>
    </section>

    <!-- Education Content -->
    <div class="max-w-5xl mx-auto space-y-8">
      <!-- University Education -->
      <div class="bg-white rounded-2xl shadow-sm border border-gray-200 p-8 hover:shadow-lg transition-shadow">
        <div class="flex flex-col md:flex-row md:items-start md:justify-between mb-6">
          <div class="flex flex-col md:flex-row items-center md:items-start gap-6 flex-1">
            <!-- University Logo -->
            <div class="relative flex-shrink-0">
              <div class="absolute -inset-2 bg-gradient-to-br from-primary-200 to-primary-100 rounded-2xl opacity-40 blur-lg"></div>
              <img 
                :src="images.osu_logo" 
                alt="Ohio State University" 
                class="relative w-24 h-24 md:w-28 md:h-28 object-contain filter drop-shadow-md" 
              />
            </div>

            <!-- University Info -->
            <div class="text-center md:text-left flex-1">
              <h2 class="text-2xl font-bold text-gray-900 mb-1">{{ education.university }}</h2>
              <h3 class="text-lg font-semibold text-primary-600 mb-3">{{ education.degree }}</h3>
              <div class="flex flex-wrap gap-3 justify-center md:justify-start">
                <span 
                  v-if="education.minor" 
                  class="inline-flex items-center px-3 py-1 bg-purple-100 text-purple-700 text-sm font-semibold rounded-lg"
                >
                  <svg class="w-4 h-4 mr-1.5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 6.253v13m0-13C10.832 5.477 9.246 5 7.5 5S4.168 5.477 3 6.253v13C4.168 18.477 5.754 18 7.5 18s3.332.477 4.5 1.253m0-13C13.168 5.477 14.754 5 16.5 5c1.747 0 3.332.477 4.5 1.253v13C19.832 18.477 18.247 18 16.5 18c-1.746 0-3.332.477-4.5 1.253"></path>
                  </svg>
                  Minor: {{ education.minor }}
                </span>
                <span 
                  v-if="education.specialization" 
                  class="inline-flex items-center px-3 py-1 bg-blue-100 text-blue-700 text-sm font-semibold rounded-lg"
                >
                  <svg class="w-4 h-4 mr-1.5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9.663 17h4.673M12 3v1m6.364 1.636l-.707.707M21 12h-1M4 12H3m3.343-5.657l-.707-.707m2.828 9.9a5 5 0 117.072 0l-.548.547A3.374 3.374 0 0014 18.469V19a2 2 0 11-4 0v-.531c0-.895-.356-1.754-.988-2.386l-.548-.547z"></path>
                  </svg>
                  Specialization: {{ education.specialization }}
                </span>
              </div>
            </div>
          </div>
          
          <span class="inline-block px-4 py-2 bg-primary-50 text-primary-700 font-semibold rounded-lg mt-4 md:mt-0 flex-shrink-0 self-center md:self-start">
            {{ education.timeline }}
          </span>
        </div>
        
        <p class="text-gray-700 leading-relaxed mb-6">
          {{ education.description }}
        </p>

        <!-- Coursework Section -->
        <div class="border-t border-gray-200 pt-6">
          <h4 class="text-lg font-bold text-gray-900 mb-4 flex items-center">
            <svg class="w-5 h-5 text-primary-600 mr-2" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 6.253v13m0-13C10.832 5.477 9.246 5 7.5 5S4.168 5.477 3 6.253v13C4.168 18.477 5.754 18 7.5 18s3.332.477 4.5 1.253m0-13C13.168 5.477 14.754 5 16.5 5c1.747 0 3.332.477 4.5 1.253v13C19.832 18.477 18.247 18 16.5 18c-1.746 0-3.332.477-4.5 1.253"></path>
            </svg>
            Relevant Coursework
          </h4>
          <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-3">
            <div 
              v-for="course in education.coursework" 
              :key="course"
              class="flex items-center bg-gray-50 rounded-lg p-3 hover:bg-gray-100 transition-colors"
            >
              <svg class="w-5 h-5 text-primary-600 mr-3 flex-shrink-0" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z"></path>
              </svg>
              <span class="text-gray-700 text-sm">{{ course }}</span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import educationData from '../data/education.json'
import imagesData from '../data/images.json'

const education = ref(educationData)
const images = ref(imagesData)
</script>
