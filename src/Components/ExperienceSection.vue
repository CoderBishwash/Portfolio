<script setup>

const ExpArray = [
    {
        id: 1,
        title: 'Computer Operator',
        org: 'Saubhagya Marketing',
        description: 'I worked as a computer operator at Saubhagya Marketing which is a Nestle products distributor. I used to work on two softwares for billing and keeping all the records of the business. I worked there from 2019 to 2024.'
    },
    {
        id: 2,
        title: 'Internship as a Front-end Developer',
        org: 'Devsign Technologies Pvt. Ltd.',
        description: 'I joined Devsign Technologies as a fornt-end intern where i got to learn variety of things about web development along with the components related to it. The timespan of me as a intern was from Nov, 2024 to May, 2025.'
    }
];

</script>
<template>

<section class="experience wrapper" id="experience">

<div class="heading" data-aos="fade-up">
    <h1>Experience</h1>
</div>

<div class="experience_description">
    <div class="experience_box" v-for="exp in ExpArray" :key="exp.id">

        <div class="bullet" data-aos="fade-up-right">

        </div>

        <div class="content_box">
            <h4 data-aos="fade-left">{{ exp.title }}</h4>
            <h3>{{ exp.org }}</h3>
            <p data-aos="fade-left">{{ exp.description }}</p>
        </div>

    </div>
</div>

</section>

</template>