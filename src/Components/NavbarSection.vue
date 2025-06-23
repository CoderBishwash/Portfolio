<script>

import { onMounted } from 'vue';

export default{
  data() {
    return {
      currentTheme: 'dark-theme', // Default theme
      showham: false
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
    ham_menu(){
      this.showham = true;
    },
    close_navbar(){
      this.showham = false;
    },
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
                        <a href="#contact">Contact</a>
                    </nav>

                    <div class="header_icons">

                      <div class="hamburger">
                                <i v-if="!showham" class="fa-solid fa-bars" @click="ham_menu()"></i>
                        </div>

                        <div class="theme" @click="toggleTheme()" style=" transition: background-color 0.3s ease, color 0.3s ease;">
                                <i v-if="currentTheme == 'light-theme'" class="fas fa-moon"></i>
                                <i v-else class="fas fa-sun" ></i>
                        </div>

                    </div>

            </header>

                    <div class="ham_navbar" data-aos="zoom-in-down" v-if="showham">
                        <!-- <img src="../images/close.png" alt="close" @click="close_navbar()"> -->
                         <i class="fa-solid fa-xmark" @click="close_navbar()" ></i>
                        <a href="#home" @click="close_navbar()">Home</a>
                        <a href="#about" @click="close_navbar()">About</a>
                        <a href="#skills" @click="close_navbar()">Skills</a>
                        <a href="#project" @click="close_navbar()">Projects & Services</a>
                        <a href="#contact" @click="close_navbar()">Contact</a>
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
    top: 8rem;
    padding: 2rem;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    gap: 2rem;
    width: 100%;
    height: 20rem;
    background-color: var(--primary-color);
    z-index: 1000;
}
.ham_navbar a{
    font-size: 1.5rem;
    color: var(--soft-black);
}
.ham_navbar i{
    width: 2.5rem;
    height: 2.5rem;
    padding: 1rem;
    font-size: 1.5rem;
    display: flex;
    justify-content: center;
    align-items: center;
    position: absolute;
    border-radius: 50%;
    background-color: var(--soft-black);
    color: var(--primary-color);
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