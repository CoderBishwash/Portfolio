<script setup>
import {ref} from 'vue';
import { Vue3Marquee } from 'vue3-marquee';

let knowledge = ref('');
let knowledgearray = ref(["HTML", "CSS", "JavaScript","TailWind CSS","Vue JS","React JS","Laravel","MySQL"]);
let bid = ref(0);
let lid = ref(0);

function displayknowledge() {
    setTimeout(() => {
        knowledge.value += knowledgearray.value[bid.value][lid.value];
        lid.value++;

        if (lid.value < knowledgearray.value[bid.value].length) {
            displayknowledge();
        } else {
            bid.value = (bid.value + 1) % knowledgearray.value.length;
            lid.value = 0;
            setTimeout(() => {
                knowledge.value = "";
                displayknowledge();
            }, 800);
        }
    }, 100);
}
displayknowledge();

</script>

<template>
    <section class="home wrapper" id="home">

<div class="image">
    <img src="../images/profile_pic.png" alt="profile_pic" data-aos="fade-right" data-aos-duration="1000">
</div>

<div class="description">
    <h1 data-aos="fade-left" data-aos-duration="500">Hi,It's <span>Bishwash</span></h1>
    <h2 data-aos="fade-left" data-aos-duration="700">I am a <span>Frontend Developer</span></h2>
    <p data-aos="fade-left" data-aos-duration="900">I'm a passionate front-end developer with a focus on creating user-centered and visually stunning websites. I excel in translating brand identities into engaging online experiences that drive results. I'm eager to contribute my skills to innovative projects and collaborate with creative teams.</p>
    <h3 data-aos="fade-left" data-aos-duration="1200">I have acquired knowledges in <span>{{ knowledge }}</span></h3>

    <Vue3Marquee :duration="10" style="width: 35rem; border-radius: 1rem;"  :clone="true">
        <div class="icons">
            <i class="fa-brands fa-html5" style="color: #E34F26;"></i>       
            <i class="fa-brands fa-css3-alt" style="color: #1572B6;"></i>    
            <i class="fa-brands fa-js" style="color: #F7DF1E;"></i>
            <img src="/src/images/tailwind.svg" style="width: 3.7rem; height: 3.7rem;" alt="tailwind">   
            <i class="fa-brands fa-vuejs" style="color: #4FC08D;"></i>       
            <i class="fa-brands fa-react" style="color: #61DAFB;"></i>
            <i class="fa-brands fa-laravel" style="color: #FF2D20;"></i>
            <i class="fas fa-database" style="color: #00758F;"></i>
    </div>
    </Vue3Marquee>
    
    
</div>



</section>
</template>