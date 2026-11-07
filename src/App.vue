<template>
  <div class="portfolio">

    <!-- Navigation Bar -->
    <header>
      <h2>AO. Portfolio</h2>

      <nav>
        <router-link to="/">Home</router-link>
        <router-link to="/about">About</router-link>
        <router-link to="/portfolio">Portfolio</router-link>
      </nav>
    </header>

    <!-- Displays the routed views -->
    <router-view />

    <!-- Footer -->
    <footer>
      <p>© 2026 Andres Orozco</p>
      <p>Built with Vue 3 + Vite</p>
    </footer>

  </div>
</template>
