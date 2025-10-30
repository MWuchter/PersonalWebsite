<template>
  <div>
    <!-- Hero Section -->
    <section class="relative bg-gradient-to-br from-primary-600 via-primary-700 to-primary-800 text-white py-20 md:py-32">
      <div class="absolute inset-0 bg-black opacity-10"></div>
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 relative z-10">
        <div class="flex flex-col md:flex-row items-center justify-center gap-12 md:gap-16">
          <!-- Profile Picture -->
          <div class="flex-shrink-0">
            <div class="relative">
              <div class="w-48 h-48 md:w-64 md:h-64 rounded-full overflow-hidden border-4 border-white shadow-2xl">
                <img 
                  :src="images.profile" 
                  :alt="personal.name" 
                  class="w-full h-full object-cover"
                  @error="handleImageError"
                />
              </div>
            </div>
          </div>
          
          <!-- Text Content -->
          <div class="text-center md:text-left max-w-2xl">
            <h1 class="text-4xl md:text-6xl font-bold mb-4 animate-fade-in">
              Hi, I'm <span class="text-primary-200">{{ personal.name }}</span>
            </h1>
            <p class="text-lg md:text-xl text-primary-100 mb-4 leading-relaxed">
              {{ personal.title }}
            </p>
            <p class="text-base md:text-lg text-primary-50 mb-8">
              {{ personal.tagline }}
            </p>
            <div class="flex flex-wrap justify-center md:justify-start gap-3">
              <router-link 
                to="/projects" 
                class="px-6 py-3 bg-white text-primary-700 rounded-lg font-bold text-base hover:bg-gray-100 transition-all shadow-lg hover:shadow-xl transform hover:-translate-y-1"
              >
                View My Projects
              </router-link>
              <a 
                :href="`mailto:${personal.email}`"
                class="inline-flex items-center px-6 py-3 border-2 border-white text-white rounded-lg font-bold text-base hover:bg-white hover:text-primary-700 transition-all shadow-lg hover:shadow-xl transform hover:-translate-y-1"
              >
                <svg class="w-5 h-5 mr-2" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z"></path>
                </svg>
                Email Me
              </a>
              <a 
                v-if="personal.github"
                :href="personal.github"
                target="_blank"
                rel="noopener noreferrer"
                class="inline-flex items-center px-6 py-3 border-2 border-white text-white rounded-lg font-bold text-base hover:bg-white hover:text-primary-700 transition-all shadow-lg hover:shadow-xl transform hover:-translate-y-1"
              >
                <svg class="w-5 h-5 mr-2" fill="currentColor" viewBox="0 0 24 24">
                  <path d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/>
                </svg>
                GitHub
              </a>
              <a 
                v-if="personal.linkedin"
                :href="personal.linkedin"
                target="_blank"
                rel="noopener noreferrer"
                class="inline-flex items-center px-6 py-3 border-2 border-white text-white rounded-lg font-bold text-base hover:bg-white hover:text-primary-700 transition-all shadow-lg hover:shadow-xl transform hover:-translate-y-1"
              >
                <svg class="w-5 h-5 mr-2" fill="currentColor" viewBox="0 0 24 24">
                  <path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433c-1.144 0-2.063-.926-2.063-2.065 0-1.138.92-2.063 2.063-2.063 1.14 0 2.064.925 2.064 2.063 0 1.139-.925 2.065-2.064 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/>
                </svg>
                LinkedIn
              </a>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Featured Projects -->
    <section class="py-20 bg-white">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="text-center mb-12">
          <h2 class="text-4xl font-bold text-gray-900 mb-4">Featured Projects</h2>
          <p class="text-xl text-gray-600 max-w-2xl mx-auto">
            Check out some of my recent work showcasing full-stack development, AI integration, and creative problem-solving
          </p>
        </div>
        <div class="grid md:grid-cols-3 gap-8 mb-12">
          <ProjectCard
            v-for="project in featuredProjects"
            :key="project.id"
            :title="project.title"
            :description="project.shortDescription"
            :link="`/projects/${project.id}`"
            :tags="project.tags.slice(0, 3)"
            :isInternal="true"
          />
        </div>
        <div class="text-center">
          <router-link 
            to="/projects" 
            class="inline-flex items-center px-8 py-4 bg-gray-900 text-white rounded-lg font-semibold text-lg hover:bg-gray-800 transition-colors shadow-lg"
          >
            View All Projects
            <svg class="w-5 h-5 ml-2" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 7l5 5m0 0l-5 5m5-5H6"></path>
            </svg>
          </router-link>
        </div>
      </div>
    </section>

    <!-- Skills Highlight -->
    <section class="py-20 bg-gradient-to-br from-gray-900 to-gray-800 text-white">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="text-center mb-16">
          <h2 class="text-4xl font-bold mb-4">Technical Skills</h2>
          <p class="text-xl text-gray-300 max-w-2xl mx-auto">
            Proficient in a wide range of modern technologies and frameworks
          </p>
        </div>
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6 mb-12">
          <div class="bg-white bg-opacity-10 backdrop-blur-sm rounded-xl p-8 hover:bg-opacity-20 transition-all hover:transform hover:scale-105 border border-white border-opacity-20">
            <div class="flex items-center mb-4">
              <div class="w-10 h-10 rounded-lg bg-blue-500 bg-opacity-20 flex items-center justify-center mr-3">
                <svg class="w-6 h-6 text-blue-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9.75 17L9 20l-1 1h8l-1-1-.75-3M3 13h18M5 17h14a2 2 0 002-2V5a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z"></path>
                </svg>
              </div>
              <h3 class="font-bold text-xl text-black">Frontend</h3>
            </div>
            <p class="text-gray-800 text-lg leading-relaxed">{{ skills.quickHighlights.frontend }}</p>
          </div>
          <div class="bg-white bg-opacity-10 backdrop-blur-sm rounded-xl p-8 hover:bg-opacity-20 transition-all hover:transform hover:scale-105 border border-white border-opacity-20">
            <div class="flex items-center mb-4">
              <div class="w-10 h-10 rounded-lg bg-green-500 bg-opacity-20 flex items-center justify-center mr-3">
                <svg class="w-6 h-6 text-green-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 12h14M5 12a2 2 0 01-2-2V6a2 2 0 012-2h14a2 2 0 012 2v4a2 2 0 01-2 2M5 12a2 2 0 00-2 2v4a2 2 0 002 2h14a2 2 0 002-2v-4a2 2 0 00-2-2m-2-4h.01M17 16h.01"></path>
                </svg>
              </div>
              <h3 class="font-bold text-xl text-black">Backend</h3>
            </div>
            <p class="text-gray-800 text-lg leading-relaxed">{{ skills.quickHighlights.backend }}</p>
          </div>
          <div class="bg-white bg-opacity-10 backdrop-blur-sm rounded-xl p-8 hover:bg-opacity-20 transition-all hover:transform hover:scale-105 border border-white border-opacity-20">
            <div class="flex items-center mb-4">
              <div class="w-10 h-10 rounded-lg bg-purple-500 bg-opacity-20 flex items-center justify-center mr-3">
                <svg class="w-6 h-6 text-purple-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9.663 17h4.673M12 3v1m6.364 1.636l-.707.707M21 12h-1M4 12H3m3.343-5.657l-.707-.707m2.828 9.9a5 5 0 117.072 0l-.548.547A3.374 3.374 0 0014 18.469V19a2 2 0 11-4 0v-.531c0-.895-.356-1.754-.988-2.386l-.548-.547z"></path>
                </svg>
              </div>
              <h3 class="font-bold text-xl text-black">AI/ML</h3>
            </div>
            <p class="text-gray-800 text-lg leading-relaxed">{{ skills.quickHighlights.aiml }}</p>
          </div>
          <div class="bg-white bg-opacity-10 backdrop-blur-sm rounded-xl p-8 hover:bg-opacity-20 transition-all hover:transform hover:scale-105 border border-white border-opacity-20">
            <div class="flex items-center mb-4">
              <div class="w-10 h-10 rounded-lg bg-orange-500 bg-opacity-20 flex items-center justify-center mr-3">
                <svg class="w-6 h-6 text-orange-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10.325 4.317c.426-1.756 2.924-1.756 3.35 0a1.724 1.724 0 002.573 1.066c1.543-.94 3.31.826 2.37 2.37a1.724 1.724 0 001.065 2.572c1.756.426 1.756 2.924 0 3.35a1.724 1.724 0 00-1.066 2.573c.94 1.543-.826 3.31-2.37 2.37a1.724 1.724 0 00-2.572 1.065c-.426 1.756-2.924 1.756-3.35 0a1.724 1.724 0 00-2.573-1.066c-1.543.94-3.31-.826-2.37-2.37a1.724 1.724 0 00-1.065-2.572c-1.756-.426-1.756-2.924 0-3.35a1.724 1.724 0 001.066-2.573c-.94-1.543.826-3.31 2.37-2.37.996.608 2.296.07 2.572-1.065z"></path>
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 12a3 3 0 11-6 0 3 3 0 016 0z"></path>
                </svg>
              </div>
              <h3 class="font-bold text-xl text-black">Tools</h3>
            </div>
            <p class="text-gray-800 text-lg leading-relaxed">{{ skills.quickHighlights.tools }}</p>
          </div>
        </div>
        <div class="text-center">
          <router-link 
            to="/skills" 
            class="inline-flex items-center px-8 py-4 bg-white text-gray-900 rounded-lg font-semibold text-lg hover:bg-gray-100 transition-colors shadow-lg"
          >
            Explore All Skills
            <svg class="w-5 h-5 ml-2" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 7l5 5m0 0l-5 5m5-5H6"></path>
            </svg>
          </router-link>
        </div>
      </div>
    </section>

    <!-- Education Highlight -->
    <section class="py-20 bg-gray-50">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="bg-white rounded-2xl shadow-lg border border-gray-200 p-8 md:p-12">
          <div class="grid md:grid-cols-2 gap-8 items-center">
            <div>
              <div class="inline-block px-4 py-2 bg-primary-100 text-primary-700 rounded-lg font-semibold mb-4">
                Education
              </div>
              <h2 class="text-3xl md:text-4xl font-bold text-gray-900 mb-4">
                {{ education.university }}
              </h2>
              <p class="text-xl text-primary-600 font-semibold mb-4">
                {{ education.degree }}
              </p>
              <div class="space-y-2 mb-6">
                <div v-if="education.minor" class="flex items-center text-gray-700">
                  <svg class="w-5 h-5 text-purple-600 mr-2" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7"></path>
                  </svg>
                  Minor in {{ education.minor }}
                </div>
                <div v-if="education.specialization" class="flex items-center text-gray-700">
                  <svg class="w-5 h-5 text-blue-600 mr-2" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7"></path>
                  </svg>
                  Specialization in {{ education.specialization }}
                </div>
                <div class="flex items-center text-gray-700">
                  <svg class="w-5 h-5 text-green-600 mr-2" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7"></path>
                  </svg>
                  Expected Graduation: {{ education.expectedGraduation }}
                </div>
              </div>
              <router-link 
                to="/education" 
                class="inline-flex items-center px-6 py-3 bg-primary-600 text-white rounded-lg font-semibold hover:bg-primary-700 transition-colors"
              >
                View Education Details
                <svg class="w-5 h-5 ml-2" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 7l5 5m0 0l-5 5m5-5H6"></path>
                </svg>
              </router-link>
            </div>
            <div class="hidden md:flex items-center justify-center">
              <div class="relative">
                <div class="absolute -inset-4 bg-gradient-to-br from-primary-200 to-primary-100 rounded-3xl opacity-50 blur-xl"></div>
                <img 
                  :src="images.osu_logo" 
                  alt="Ohio State University" 
                  class="relative w-48 h-48 object-contain filter drop-shadow-lg hover:scale-105 transition-transform duration-300" 
                />
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

  </div>
</template>

<script setup>
import { ref } from 'vue'
import ProjectCard from '../components/ProjectCard.vue'
import projectsData from '../data/projects.json'
import personalData from '../data/personal.json'
import educationData from '../data/education.json'
import skillsData from '../data/skills.json'
import imagesData from '../data/images.json'

const personal = ref(personalData)
const education = ref(educationData)
const skills = ref(skillsData)
const images = ref(imagesData)
const featuredProjects = ref(projectsData.slice(0, 3))

const handleImageError = (e) => {
  // Fallback to a placeholder if image fails to load
  e.target.src = 'https://via.placeholder.com/300x300/6366f1/ffffff?text=Profile'
}
</script>
