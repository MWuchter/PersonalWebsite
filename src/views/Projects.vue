<template>
  <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-12">
    <!-- Hero Section -->
    <section class="text-center py-12 mb-12">
      <h1 class="text-5xl font-bold text-gray-900 mb-4">Projects</h1>
      <p class="text-xl text-gray-600 max-w-2xl mx-auto">
        A collection of things I've built — from web applications to game systems and AI experiments
      </p>
    </section>

    <!-- Projects Grid -->
    <section class="grid md:grid-cols-2 lg:grid-cols-3 gap-6">
      <ProjectCard
        v-for="project in projects"
        :key="project.id"
        :title="project.title"
        :description="project.shortDescription || project.description"
        :link="`/projects/${project.id}`"
        :tags="project.tags"
        :isInternal="true"
      />
    </section>
  </div>
</template>

<script setup>
import ProjectCard from '../components/ProjectCard.vue'
import projects from '../data/projects.json'
</script>
