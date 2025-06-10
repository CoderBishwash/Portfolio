<script setup>
import { onMounted } from 'vue';
import Navbar from './Components/NavbarSection.vue';
import HomeSection from './Components/HomeSection.vue';
import AboutSection from './Components/AboutSection.vue';
import SkillsSection from './Components/SkillsSection.vue';
import ProjectServicesSection from './Components/Project&ServicesSection.vue';
import EducationSection from './Components/EducationSection.vue';
import ExperienceSection from './Components/ExperienceSection.vue';
import ContactSection from './Components/ContactSection.vue';
import FooterSection from './Components/FooterSection.vue';
import AOS from 'aos';


onMounted(()=>{
  AOS.init();
});

</script>
<template>

  <!-- Navbar -->
    <Navbar />
  <!-- ----------- -->

  <!-- Home Section -->
    <HomeSection />
  <!-- ----------- -->

<div class="line"></div>

  <!-- About me Section -->
    <AboutSection />
  <!-- ----------- -->

<div class="line"></div>

  <!-- Skills Section -->
    <SkillsSection />
  <!-- ----------- -->

<div class="line"></div>

  <!-- Projects & Services -->
    <ProjectServicesSection />
  <!-- ----------- -->

<div class="line"></div>

  <!-- Education Section -->
    <EducationSection />
  <!-- ----------- -->

<div class="line"></div>

  <!-- Experience Section -->
    <ExperienceSection />
  <!-- ----------- -->

<div class="line"></div>

  <!-- Contact Section -->
    <ContactSection />
  <!-- ----------- -->

  <!-- Footer Section-->
    <FooterSection />
  <!-- ----------- -->

</template>