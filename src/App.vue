<script setup>
import profilePhoto from './assets/profile.png'
</script>

<template>
  <div class="portfolio">

    <!-- Navigation Bar -->
    <header>
      <h2>AO. Portfolio</h2>

      <nav>
        <a href="#home">Home</a>
        <a href="#about">About</a>
        <a href="#projects">Projects</a>
        <a href="#skills">Skills</a>
        <a href="Resume">Resume</a>
        <a href="#contact">Contact</a>
      </nav>
    </header>

    <!-- Home Page -->
    <main id="home">
      <section class="hero">

        <!-- Introduction -->
        <div class="hero-text">
          <p>Welcome to my portfolio!</p>

          <h1>Hi, I'm Andres Orozco</h1>

          <h3>Aspiring Developer & IT Professional</h3>

          <p>
            I'm passionate about technology and constantly seeking to expand 
            my knowledge and skills in the field of software development. 
            I enjoy working on challenging projects that allow me to grow 
            as a developer and contribute to innovative solutions.
            I am currently pursuing an associates degree of Applied Sciences
            in Information Technology & Systems.
          </p>
        </div>

        <!-- Professional Photo -->
        <div class="hero-image">
          <img :src="profilePhoto" alt="Professional photo of Andres Orozco">
        </div>

      </section>
    </main>

    <!-- Footer -->
    <footer>
      <p>© 2026 Andres Orozco</p>
      <p>Built with Vue 3 + Vite</p>
    </footer>

  </div>
</template>
