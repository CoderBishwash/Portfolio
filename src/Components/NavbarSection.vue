<script>

import { ref,onMounted } from 'vue';


let showham = ref(false);
let ham_menu = () => {
    showham.value = true;
}

let close_navbar = () => {
    showham.value = false;
}
export default{
  data() {
    return {
      currentTheme: 'light-theme', // Default theme
    };
  },
  mounted() {
    // Checking local storage for a saved theme when the component mounts
    const savedTheme = localStorage.getItem('userTheme');
    if (savedTheme) {
      this.currentTheme = savedTheme;
      this.applyTheme(savedTheme);
    } else {
      // If no theme is saved, apply the default theme
      this.applyTheme(this.currentTheme);
    }
  },
  methods: {
    toggleTheme() {
      // Toggle the theme
      this.currentTheme = this.currentTheme === 'light-theme' ? 'dark-theme' : 'light-theme';
      
      // Save the new theme to local storage
      localStorage.setItem('userTheme', this.currentTheme);
      
      // Apply the theme to the DOM
      this.applyTheme(this.currentTheme);
    },
    applyTheme(theme) {
      // Apply CSS classes to the <body> element (or your root element)
      // where you would link your CSS styles.
      document.body.classList.remove('light-theme', 'dark-theme'); // Remove existing
      document.body.classList.add(`${theme}`); // Add the new one
    },
  },
};

</script>
<template>
            <header>

                    <div class="logo">
                        <a href="#home">BishWash</a>
                    </div>

                    <nav>
                        <a href="#home">Home</a>
                        <a href="#about">About</a>
                        <a href="#skills">Skills</a>
                        <a href="#project">Projects & Services</a>
                        <a href="#education">Education</a>
                        <a href="#experience">Experience</a>
                        <a href="#contact">Contact</a>
                    </nav>

                    <div class="header_icons">
                        <div class="theme" @click="toggleTheme()">
                                <i v-if="userTheme == 'light-theme'" class="fas fa-moon"></i>
                                <i v-else class="fas fa-sun" ></i>
                        </div>

                        <div class="hamburger">
                                <i v-if="!showham" class="fa-solid fa-bars" @click="ham_menu()"></i>
                        </div>
                    </div>

            </header>

                    <div class="ham_navbar animate__animated animate__fadeInRight" v-if="showham">
                        <img src="../images/close.png" alt="close" @click="close_navbar()">
                        <a href="#home">Home</a>
                        <a href="#about">About</a>
                        <a href="#skills">Skills</a>
                        <a href="#project">Projects & Services</a>
                        <a href="#education">Education</a>
                        <a href="#experience">Experience</a>
                        <a href="#contact">Contact</a>
                    </div>
</template>
<style scoped>
.hamburger{
    font-size: 2.5rem;
    color: var(--primary-color);
}
.ham_navbar{
    position: fixed;
    right: 0;
    top: 11rem;
    padding: 2rem;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    gap: 2rem;
    width: 20rem;
    height: 30rem;
    border-radius: 2rem;
    background-color: var(--primary-color);
    z-index: 1000;
}
.ham_navbar a{
    font-size: 1.5rem;
    color: var(--soft-black);
}
.ham_navbar img{
    width: 2rem;
    height: 2rem;
    position: absolute;
    border-radius: 50%;
    background-color: #333;
    top: 1rem;
    right: 1rem;
}
.theme{
    width: 3rem;
    height: 3rem;
    border-radius: 50%;
    transition: .8s ease;
    display: flex;
    align-items: center;
    justify-content: center;
}
.theme i{
    font-size: 2rem;
    color: white;
}
.theme:hover{
    background-color: var(--primary-color);
}
.header_icons{
    display: flex;
    align-items: center;
    gap: 5rem;
}
</style>