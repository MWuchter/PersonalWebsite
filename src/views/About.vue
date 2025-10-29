<template>
  <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-12">
    <!-- Hero Section -->
    <section class="text-center py-12 mb-16">
      <h1 class="text-5xl font-bold text-gray-900 mb-4">About Me</h1>
      <p class="text-2xl text-primary-600 font-medium">Developer, Creator, and Lifelong Learner</p>
    </section>

    <!-- Software Developer & AI Enthusiast Section -->
    <section class="mb-20">
      <div class="grid md:grid-cols-2 gap-12 items-center">
        <div class="order-2 md:order-1">
          <h2 class="text-4xl font-bold text-gray-900 mb-6">Software Developer & AI Enthusiast</h2>
          <p class="text-lg text-gray-700 leading-relaxed mb-4">
            I'm a passionate software developer with a deep interest in artificial intelligence. 
            Much of the code I write is AI-assisted, and I'm fascinated by the ways machine 
            learning can accelerate creativity and productivity.
          </p>
          <p class="text-lg text-gray-700 leading-relaxed">
            My long-term goal is to get more involved in training and testing large AI models, 
            building systems that make advanced technology more accessible and powerful.
          </p>
        </div>
        <div class="order-1 md:order-2">
          <div class="aspect-square rounded-2xl overflow-hidden shadow-lg">
            <img :src="images.photo_of_me1" alt="Software Developer" class="w-full h-full object-cover" />
          </div>
        </div>
      </div>
    </section>

    <!-- Integrating AI Into the Everyday Section -->
    <section class="mb-20">
      <div class="grid md:grid-cols-2 gap-12 items-center">
        <div>
          <div class="aspect-square rounded-2xl overflow-hidden shadow-lg">
            <img :src="images.hackathon_photo" alt="AI Integration" class="w-full h-full object-cover" />
          </div>
        </div>
        <div>
          <h2 class="text-4xl font-bold text-gray-900 mb-6">Integrating AI Into the Everyday</h2>
          <p class="text-lg text-gray-700 leading-relaxed mb-4">
            I'm particularly interested in bridging the gap between cutting-edge AI research 
            and practical applications. I love exploring how intelligent systems can enhance 
            user experiences, automate complex workflows, and transform traditional industries.
          </p>
          <p class="text-lg text-gray-700 leading-relaxed">
            Whether it's through web apps, automation tools, or experimental projects, I'm 
            always looking for new ways to integrate AI into real-world solutions.
          </p>
        </div>
      </div>
    </section>

    <!-- Craftsmanship & Creativity Section -->
    <section class="mb-20">
      <div class="grid md:grid-cols-2 gap-12 items-center">
        <div class="order-2 md:order-1">
          <h2 class="text-4xl font-bold text-gray-900 mb-6">Craftsmanship & Creativity</h2>
          <p class="text-lg text-gray-700 leading-relaxed mb-4">
            Outside of coding, I find balance through woodworking. There's something deeply 
            satisfying about transforming raw materials into something functional and beautiful.
          </p>
          <p class="text-lg text-gray-700 leading-relaxed">
            As an Eagle Scout, I've always appreciated hands-on problem-solving and the value 
            of persistence — qualities that translate directly into my approach to software 
            development.
          </p>
        </div>
        <div class="order-1 md:order-2">
          <div class="aspect-square rounded-2xl overflow-hidden shadow-lg">
            <img :src="images.woodworking_photo" alt="Woodworking and Craftsmanship" class="w-full h-full object-cover" />
          </div>
        </div>
      </div>
    </section>

    <!-- Entrepreneurship & Ambition Section -->
    <section class="mb-12">
      <div class="grid md:grid-cols-2 gap-12 items-center">
        <div>
          <div class="aspect-square rounded-2xl overflow-hidden shadow-lg">
            <img :src="images.photo_of_me2" alt="Entrepreneurship" class="w-full h-full object-cover" />
          </div>
        </div>
        <div>
          <h2 class="text-4xl font-bold text-gray-900 mb-6">Entrepreneurship & Ambition</h2>
          <p class="text-lg text-gray-700 leading-relaxed mb-4">
            I'm driven by an entrepreneurial mindset and a passion for building things that 
            last — whether that's a startup, a side project, or a digital product.
          </p>
          <p class="text-lg text-gray-700 leading-relaxed">
            I enjoy combining my technical skills with business strategy to create innovative, 
            profitable ventures. I'm constantly looking for opportunities to learn, grow, and 
            turn ideas into reality.
          </p>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import imagesData from '../data/images.json'

const images = ref(imagesData)
</script>
