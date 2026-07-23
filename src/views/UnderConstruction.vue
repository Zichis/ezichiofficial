<script setup lang="ts">
import { ref, onMounted } from 'vue'

const progress = ref(0)
const currentYear = new Date().getFullYear()

onMounted(() => {
  const interval = setInterval(() => {
    progress.value = Math.min(progress.value + 1, 100)
    if (progress.value >= 100) clearInterval(interval)
  }, 60)
})
</script>

<template>
  <div class="page">
    <div class="bg-grid" />

    <div class="hero">
      <div class="badge">
        <span class="badge-dot" />
        Under Construction
      </div>

      <h1 class="title">
        Something
        <span class="gradient-text">amazing</span>
        is coming
      </h1>

      <p class="subtitle">
        I'm crafting a brand new portfolio experience. Stay tuned for
        something built with care.
      </p>

      <div class="progress-wrapper">
        <div class="progress-label">
          <span>Progress</span>
          <span>{{ progress }}%</span>
        </div>
        <div class="progress-track">
          <div class="progress-bar" :style="{ width: progress + '%' }" />
        </div>
      </div>

      <div class="actions">
        <a href="mailto:hello@ezichi.dev" class="btn btn-primary">
          <svg
            width="18"
            height="18"
            viewBox="0 0 24 24"
            fill="none"
            stroke="currentColor"
            stroke-width="2"
            stroke-linecap="round"
            stroke-linejoin="round"
          >
            <rect x="2" y="4" width="20" height="16" rx="2" />
            <path d="m22 7-8.97 5.7a1.94 1.94 0 0 1-2.06 0L2 7" />
          </svg>
          Get in touch
        </a>
        <a
          href="https://github.com/ezichi"
          target="_blank"
          rel="noopener noreferrer"
          class="btn btn-outline"
        >
          <svg
            width="18"
            height="18"
            viewBox="0 0 24 24"
            fill="currentColor"
          >
            <path
              d="M12 0C5.37 0 0 5.37 0 12c0 5.31 3.435 9.795 8.205 11.385.6.105.825-.255.825-.57 0-.285-.015-1.23-.015-2.235-3.015.555-3.795-.735-4.035-1.41-.135-.345-.72-1.41-1.23-1.695-.42-.225-1.02-.78-.015-.795.945-.015 1.62.87 1.845 1.23 1.08 1.815 2.805 1.305 3.495.99.105-.78.42-1.305.765-1.605-2.67-.3-5.46-1.335-5.46-5.925 0-1.305.465-2.385 1.23-3.225-.12-.3-.54-1.53.12-3.18 0 0 1.005-.315 3.3 1.23.96-.27 1.98-.405 3-.405s2.04.135 3 .405c2.295-1.56 3.3-1.23 3.3-1.23.66 1.65.24 2.88.12 3.18.765.84 1.23 1.905 1.23 3.225 0 4.605-2.805 5.625-5.475 5.925.435.375.81 1.095.81 2.22 0 1.605-.015 2.895-.015 3.3 0 .315.225.69.825.57A12.02 12.02 0 0 0 24 12c0-6.63-5.37-12-12-12Z"
            />
          </svg>
          GitHub
        </a>
      </div>
    </div>

    <footer class="footer">
      &copy; {{ currentYear }} Ezichi. All rights reserved.
    </footer>
  </div>
</template>

<style>
*,
*::before,
*::after {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>

<style scoped>
.page {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  background: #0a0a0b;
  color: #fafafa;
  position: relative;
  overflow: hidden;
  padding: 2rem;
}

.bg-grid {
  position: absolute;
  inset: 0;
  background-image: radial-gradient(rgba(255, 255, 255, 0.04) 1px, transparent 1px);
  background-size: 32px 32px;
  mask-image: radial-gradient(ellipse 50% 50% at 50% 50%, black 30%, transparent 70%);
  -webkit-mask-image: radial-gradient(ellipse 50% 50% at 50% 50%, black 30%, transparent 70%);
  pointer-events: none;
}

.hero {
  position: relative;
  text-align: center;
  max-width: 560px;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 1.5rem;
}

.badge {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  padding: 0.375rem 1rem;
  border-radius: 9999px;
  font-size: 0.8rem;
  font-weight: 500;
  letter-spacing: 0.02em;
  background: rgba(255, 255, 255, 0.06);
  border: 1px solid rgba(255, 255, 255, 0.08);
  color: rgba(255, 255, 255, 0.7);
}

.badge-dot {
  width: 6px;
  height: 6px;
  border-radius: 50%;
  background: #22c55e;
  animation: pulse-dot 2s ease-in-out infinite;
}

@keyframes pulse-dot {
  0%,
  100% {
    opacity: 1;
  }
  50% {
    opacity: 0.3;
  }
}

.title {
  font-size: clamp(2.25rem, 6vw, 3.75rem);
  font-weight: 800;
  line-height: 1.1;
  letter-spacing: -0.03em;
}

.gradient-text {
  background: linear-gradient(135deg, #a78bfa, #60a5fa, #34d399);
  -webkit-background-clip: text;
  background-clip: text;
  -webkit-text-fill-color: transparent;
}

.subtitle {
  font-size: 1.05rem;
  line-height: 1.7;
  color: rgba(255, 255, 255, 0.5);
  max-width: 420px;
}

.progress-wrapper {
  width: 100%;
  max-width: 320px;
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.progress-label {
  display: flex;
  justify-content: space-between;
  font-size: 0.8rem;
  color: rgba(255, 255, 255, 0.4);
  font-weight: 500;
}

.progress-track {
  width: 100%;
  height: 6px;
  background: rgba(255, 255, 255, 0.06);
  border-radius: 9999px;
  overflow: hidden;
}

.progress-bar {
  height: 100%;
  border-radius: 9999px;
  background: linear-gradient(90deg, #a78bfa, #60a5fa, #34d399);
  transition: width 0.3s ease;
}

.actions {
  display: flex;
  gap: 0.75rem;
  flex-wrap: wrap;
  justify-content: center;
  margin-top: 0.5rem;
}

.btn {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  padding: 0.75rem 1.5rem;
  border-radius: 9999px;
  font-size: 0.9rem;
  font-weight: 600;
  text-decoration: none;
  transition: all 0.2s ease;
  cursor: pointer;
  border: none;
}

.btn-primary {
  background: #fafafa;
  color: #0a0a0b;
}

.btn-primary:hover {
  background: #e5e5e5;
  transform: translateY(-1px);
}

.btn-outline {
  background: transparent;
  color: #fafafa;
  border: 1px solid rgba(255, 255, 255, 0.15);
}

.btn-outline:hover {
  background: rgba(255, 255, 255, 0.06);
  border-color: rgba(255, 255, 255, 0.25);
  transform: translateY(-1px);
}

.footer {
  position: absolute;
  bottom: 2rem;
  font-size: 0.8rem;
  color: rgba(255, 255, 255, 0.25);
}
</style>
