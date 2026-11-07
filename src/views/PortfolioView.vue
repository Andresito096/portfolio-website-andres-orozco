<script setup>
import { ref, onMounted } from 'vue'

// Reactive state for the portfolio view
const repositories = ref([])
const loading = ref(true)
const error = ref('')

// GitHub username
const githubUsername = 'Andresito096'

// Fetch repositories from GitHub API
async function fetchRepositories() {
  loading.value = true
  error.value = ''

  try {
    const response = await fetch(`https://api.github.com/users/${githubUsername}/repos?per_page=100&sort=updated`)

    if (!response.ok) {
      throw new Error('Unable to retrieve repositories.')
    }

    repositories.value = await response.json()
  } catch (err) {
    error.value = 'Sorry, my GitHub projects could not be retrieved. Please try again later.'
    console.error('GitHub API error:', err)
  } finally {
    loading.value = false
  }
}

// Fetch repositories when the page opens
onMounted(() => {
  fetchRepositories()
})
</script>

<template> 
    <main class="portfolio-page">
        <div class="portfolio-container">
            
            <section class="portfolio-intro">
                <h1>Welcome to My Portfolio</h1>
                <p>
                    Here you can find a collection of my GitHub repositories and projects. Feel free to explore and learn more about my work.
                    This page will automatically display my public repositories from GitHub and stay up-to-date as I continue to create and 
                    develop new projects.
                </p>
            </section>

            <!-- Loading Message -->
            <p v-if="loading" class="portfolio-message">
                Loading GitHub repositories...
            </p>

            <!-- Error Message -->
             <p v-else-if="error" class="portfolio-message">
                {{ error }}
            </p>

            <!-- Repositories List -->
            <div v-else class="repository-grid">
                <div
                    v-for="repo in repositories"
                    :key="repo.id"
                    class="repository-card"
                >
                    <h2>
                        <a
                            :href="repo.html_url"
                            target="_blank"
                            rel="noopener noreferrer"
                        >
                            {{ repo.name }}
                        </a>
                    </h2>

                    <p>
                        {{ repo.description || 'No description available.' }}
                    </p>

                    <div class="repository-details">
                        <span>
                            language: {{ repo.language || 'Not specified' }}
                        </span>

                        <span>
                            Updated:
                            {{ new Date(repo.updated_at).toLocaleDateString() }}
                        </span>
                    </div>
                </div>
            </div>

        </div>
    </main>
</template>
