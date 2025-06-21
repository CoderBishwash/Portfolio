<script setup>

import { ref } from 'vue';
import EducationSection from './EducationSection.vue';
import ExperienceSection from './ExperienceSection.vue';

let showContent = ref(true);
const showContents = () => {
    showContent.value = !showContent.value;
}
let paragraph = ref(false);
const toggleparagraph = () =>{
  paragraph.value = !paragraph.value;
}

</script>
<template>

<section class="about wrapper" id="about" >

<div class="heading">
    <h1 data-aos="fade-in">About me</h1>
</div>

<div class="desc">
    <p data-aos="fade-in">I create the visual and interactive parts of websites—everything you see and click on. I use modern tools like Vue.js and React to build fast, responsive, and user-friendly experiences. My goal is to make sure what I build not only looks great but also works smoothly and is intuitive for anyone using it. I'm always learning new ways to make these experiences even better.</p>
    <p v-if="paragraph" data-aos="fade-in">I have had keen interest in designing and developing webpages and websites for quite a long time. I specialize in transforming design concepts into responsive, high-performance, and accessible websites. With a strong command of HTML, CSS, and JavaScript, I'm dedicated to crafting clean, efficient code that not only looks great but also delivers seamless user interactions. My expertise also extends to Nuxt.js for server-rendered Vue applications and Android Studio for mobile development, offering a versatile skill set</p>
</div>

<div class="read_more" data-aos="fade-in" @click="toggleparagraph()">
  <a v-if="paragraph">See less...</a>
    <a v-else>Read more...</a>
</div>

<div class="edu-exp">

    <div class="title" @click="showContents()">
        <h1 :class="showContent? 'active': ''" data-aos="fade-in" >Education</h1>
        <h1 :class="!showContent? 'active': ''" data-aos="fade-in" >Experience</h1>
    </div>

    <div class="components">
        <EducationSection v-if="showContent" />
        <ExperienceSection v-else />
    </div>
  
</div>

<div class="details">
    <div class="social-accounts" data-aos="fade-in">
        <a href="https://www.linkedin.com/in/bishwash-pokharel-361450337/" target="_blank"><i class="fa-brands fa-linkedin"></i></a>
        <a href="https://github.com/CoderBishwash" target="_blank"><i class="fa-brands fa-github"></i></a>
        <a href="https://www.instagram.com/__bishwash_/" target="_blank"><i class="fa-brands fa-instagram"></i></a>
        <a href="https://mail.google.com/mail/?view=cm&fs=1&to=kxakhabar54@gmail.com&su=Your%20Subject%20Here&body=Your%20email%20body%20goes%20here" target="_blank"><i class="fas fa-envelope"></i></a>
    </div>
    <div class="cv" data-aos="fade-in">
        <a href="/images/CV.pdf" download="Bishwash's_CV">Download CV</a>
        <a href="https://wa.me/9779817241033?text=I%27m%20interested%20in%20your%20services" target="_blank">Hire me</a>
    </div>
</div>

</section>

</template>

<style scoped>
.about .edu-exp{
    display: flex;
    flex-direction: column;
    justify-content: center;
    margin-top: 2rem;
}
.about .edu-exp .title{
    display: flex;
    justify-content: space-around;
    align-items: center;
}
.about .edu-exp .title h1{
    font-size: 2.5rem;
    cursor: pointer;
}
.active{
    border-bottom: .2rem solid var(--primary-color);
    color: var(--primary-color);
}
</style>