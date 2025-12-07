<script setup>
import { ref } from 'vue';
import vrImg from "../images/vr.jpg"
import aiImg from "../images/ai.jpg"

let ProjectArray = ref([
  {
    id: 1,
    title: 'Demo Clothing Website',
    description: 'HTML - CSS - VUEJS with user interactive interfaces',
    image: '../images/clothing.jpg',
    projLink: 'https://github.com/CoderBishwash/Demo-Clothing-Website',
    active: false
  },
  {
    id: 2,
    title: 'A Simple Chatlist Interface',
    description: 'HTML - CSS - VUEJS - PINIA with features to add, edit, delete data',
    image: '../images/chatlist.jpg',
    projLink: 'https://github.com/CoderBishwash/Simple-Chatlist',
    active: false
  },
  {
    id: 3,
    title: 'An E-commerce Website',
    description: 'HTML - CSS - VUEJS - PINIA - VUE-ROUTER - AXIOS with features to add products to cart, wishlist',
    image: '../images/e-commerce.jpg',
    projLink: 'https://github.com/CoderBishwash/E-Commerce-Website',
    active: false
  },
  {
    id: 4,
    title: 'A Virtual Reality Website',
    description: 'TAILWIND CSS - REACT JS',
    image: vrImg,
    projLink: 'https://github.com/CoderBishwash/Virtual-reality-website',
    active: false
  },
  {
    id: 5,
    title: 'A Simple AI Assistant',
    description: 'Local AI Chatbot (React/Laravel/Ollama). Full-stack assistant using Ollama for local processing, featuring Voice Input and Auto-Titled History.',
    image: aiImg,
    projLink: 'https://github.com/CoderBishwash/AI-Assistant',
    active: false
  },
]);

let ServicesArray = [
    {
      id: 1,
      img:'../images/fullstack.png',
      title: 'Full-Stack Web Application Development',
      description: 'I build scalable web apps using Vue.js and Nuxt.js for frontend, paired with Laravel and MySQL for backend development — delivering seamless, full-featured solutions.'
    },
    {
      id: 2,
      img: '../images/front-end.png',
      title: 'Frontend Development (Vue + Nuxt + Tailwind CSS)',
      description: 'Creating modern, responsive, and interactive UIs with Vue, Nuxt, and Tailwind CSS. I also use Pinia for clean and efficient state management in large-scale applications.'
    },
    {
      id: 3,
      img: '../images/back-end.png',
      title: 'Backend Development (Laravel + MySQL)',
      description: 'Developing secure and high-performing RESTful APIs and database-driven logic with Laravel and MySQL — optimized for speed and scalability.'
    },
    {
      id: 4,
      img:'../images/api.png',
      title: 'API Integration (Axios + 3rd Party Services)',
      description: 'Using Axios to connect frontend apps with REST APIs, integrate services like EmailJS (for contact forms), CRMs, or any external data source.'
    },
   {
      id: 5,
      img: '../images/mobile-app.png',
      title: 'Mobile application (Android Studio)',
      description: 'I offer native Android app development using Java and Android Studio. Whether you need a simple utility app or a complete mobile solution, I create apps that are fast, responsive, and user-friendly.' 
    },
  ];

  let ShowProj = (projects) => {
      ProjectArray.value.map((element)=>{
        if(projects.id == element.id) element.active = !element.active;
        });
      }

</script>

<template>

<section class="proj_services wrapper" id="project">

<div class="heading" data-aos="fade-in">
    <h1>Projects & Services</h1>
</div>

<div class="project_container">
    <h2 data-aos="fade-right"> <div class="bullet"></div>Some of my projects</h2>
    <ul>
            <li v-for="projects in ProjectArray" :key="projects.id" data-aos="fade-in" @click="ShowProj(projects)">
              <div class="title">
                        <h3>{{ projects.title }}</h3>
                        <span>
                            <i v-if="projects.active" class="fas fa-chevron-up"></i>
                            <i v-else class="fas fa-chevron-right"></i>
                        </span>
                    </div>
                    <div class="contents" v-if="projects.active" data-aos="zoom-in">

                      <div class="image">
                          <img :src="projects.image" alt="1">
                        </div>
                            <p> {{ projects.description }}</p>
                            <div class="btn">
                                <a :href="projects.projLink" target="_blank">Show Project</a>
                            </div>

                    </div>
            </li>
    </ul>
</div>

<div class="services_container">
    <h2 data-aos="fade-right"> <div class="bullet"></div>Services</h2>

    <ul>
        <li v-for="services in ServicesArray" :key="services.id" data-aos="fade-in">
            <img :src="services.img" :alt="services.img">
            <h3>{{ services.title }}</h3>
            <p>{{ services.description }}</p>
        </li>
    </ul>
</div>

</section>

</template>