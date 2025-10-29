<template>
  <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-12">
    <!-- Hero Section -->
    <section class="text-center py-12 mb-12">
      <h1 class="text-5xl font-bold text-gray-900 mb-4">Skills</h1>
      <p class="text-xl text-gray-600 max-w-2xl mx-auto">
        Technologies and tools I work with to build great software
      </p>
    </section>

    <!-- Skills Categories -->
    <div class="space-y-12">
      <section v-for="category in skills.categories" :key="category.name">
        <div class="flex items-center mb-6">
          <div class="w-12 h-12 bg-primary-100 rounded-lg flex items-center justify-center mr-4">
            <svg class="w-6 h-6 text-primary-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path 
                v-if="category.icon === 'frontend'"
                stroke-linecap="round" 
                stroke-linejoin="round" 
                stroke-width="2" 
                d="M9.75 17L9 20l-1 1h8l-1-1-.75-3M3 13h18M5 17h14a2 2 0 002-2V5a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z"
              ></path>
              <path 
                v-else-if="category.icon === 'backend'"
                stroke-linecap="round" 
                stroke-linejoin="round" 
                stroke-width="2" 
                d="M5 12h14M5 12a2 2 0 01-2-2V6a2 2 0 012-2h14a2 2 0 012 2v4a2 2 0 01-2 2M5 12a2 2 0 00-2 2v4a2 2 0 002 2h14a2 2 0 002-2v-4a2 2 0 00-2-2m-2-4h.01M17 16h.01"
              ></path>
              <path 
                v-else-if="category.icon === 'ai'"
                stroke-linecap="round" 
                stroke-linejoin="round" 
                stroke-width="2" 
                d="M9.663 17h4.673M12 3v1m6.364 1.636l-.707.707M21 12h-1M4 12H3m3.343-5.657l-.707-.707m2.828 9.9a5 5 0 117.072 0l-.548.547A3.374 3.374 0 0014 18.469V19a2 2 0 11-4 0v-.531c0-.895-.356-1.754-.988-2.386l-.548-.547z"
              ></path>
              <path 
                v-else-if="category.icon === 'game'"
                stroke-linecap="round" 
                stroke-linejoin="round" 
                stroke-width="2" 
                d="M14.752 11.168l-3.197-2.132A1 1 0 0010 9.87v4.263a1 1 0 001.555.832l3.197-2.132a1 1 0 000-1.664z M21 12a9 9 0 11-18 0 9 9 0 0118 0z"
              ></path>
              <path 
                v-else-if="category.icon === 'tools'"
                stroke-linecap="round" 
                stroke-linejoin="round" 
                stroke-width="2" 
                d="M10.325 4.317c.426-1.756 2.924-1.756 3.35 0a1.724 1.724 0 002.573 1.066c1.543-.94 3.31.826 2.37 2.37a1.724 1.724 0 001.065 2.572c1.756.426 1.756 2.924 0 3.35a1.724 1.724 0 00-1.066 2.573c.94 1.543-.826 3.31-2.37 2.37a1.724 1.724 0 00-2.572 1.065c-.426 1.756-2.924 1.756-3.35 0a1.724 1.724 0 00-2.573-1.066c-1.543.94-3.31-.826-2.37-2.37a1.724 1.724 0 00-1.065-2.572c-1.756-.426-1.756-2.924 0-3.35a1.724 1.724 0 001.066-2.573c-.94-1.543.826-3.31 2.37-2.37.996.608 2.296.07 2.572-1.065z M15 12a3 3 0 11-6 0 3 3 0 016 0z"
              ></path>
            </svg>
          </div>
          <h2 class="text-3xl font-bold text-gray-900">{{ category.name }}</h2>
        </div>
        <div class="grid md:grid-cols-2 lg:grid-cols-4 gap-6">
          <SkillCard 
            v-for="skill in category.skills"
            :key="skill.name"
            :title="skill.name" 
            :description="skill.description"
          />
        </div>
      </section>
    </div>
  </div>
</template>

<script setup>
import { ref, defineComponent, h } from 'vue'
import skillsData from '../data/skills.json'

const skills = ref(skillsData)

// Inline SkillCard component
const SkillCard = defineComponent({
  props: {
    title: String,
    description: String
  },
  setup(props) {
    return () => h('div', 
      { class: 'bg-white rounded-xl border border-gray-200 p-6 hover:shadow-lg transition-all duration-300 group' },
      [
        h('h3', { class: 'text-lg font-bold text-gray-900 mb-2' }, props.title),
        h('p', { class: 'text-gray-600 text-sm leading-relaxed' }, props.description)
      ]
    )
  }
})
</script>
