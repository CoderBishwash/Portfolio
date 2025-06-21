<script setup>

const EduArray = [
    {
        id: 1,
        title: 'SEE (Secondary Education Examination)',
        description: 'Samata Shikshya Niketan',
        date: '2074',
        grade: 'Grade: 3.65',
        image: '../images/passed.png'
    },
    {
        id: 2,
        title: '+2 (Computer Science)',
        description: 'Oxford College of Engineering and Management',
        date: '2075 - 2077',
        grade: 'Grade: 3.17',
        image: '../images/passed.png'
    },
    {
        id: 3,
        title: 'BCA (Bachelor in Computer Application)',
        description: 'Oxford College of Engineering and Management',
        date: '2077 - Present',
        grade: 'Studying',
        image: '../images/studying.png'
    }
];

</script>
<template>

<section class="education wrapper" id="education">

<div class="education_description">

    <div class="education_box" v-for="edu in EduArray" :key="edu.id">

        <div class="bullet" data-aos="fade-right">

        </div>

        <div class="content_box">
            <h4 data-aos="fade-in">{{ edu.title }}</h4>
            <h3>{{ edu.description }}</h3>
            <div class="grade" data-aos="fade-in">
                <p>{{ edu.date }}</p>
                <span>
                    <img :src="edu.image" :alt="edu.image">
                    <strong>{{ edu.grade }}</strong>
                </span>
            </div>
        </div>

    </div>

</div>

</section>
</template>