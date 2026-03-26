<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue'

const scrolled = ref(false)
const mobileOpen = ref(false)

function onScroll() {
  scrolled.value = window.scrollY > 40
}

onMounted(() => window.addEventListener('scroll', onScroll, { passive: true }))
onUnmounted(() => window.removeEventListener('scroll', onScroll))

const links = [
  { to: '/', label: 'Home' },
  { to: '/leistungen', label: 'Leistungen' },
  { to: '/ueber-mich', label: 'Über mich' },
  { to: '/kontakt', label: 'Kontakt' },
]
</script>

<template>
  <header class="navbar" :class="{ scrolled, 'mobile-open': mobileOpen }">
    <div class="navbar__inner container">
      <router-link to="/" class="navbar__brand" @click="mobileOpen = false">
        <span class="brand-name">Angela Einicke</span>
        <span class="brand-title">Diplom-Psychologin</span>
      </router-link>

      <button
        class="navbar__toggle"
        :class="{ active: mobileOpen }"
        @click="mobileOpen = !mobileOpen"
        aria-label="Menü"
      >
        <span></span>
        <span></span>
        <span></span>
      </button>

      <nav class="navbar__nav" :class="{ open: mobileOpen }">
        <router-link
          v-for="link in links"
          :key="link.to"
          :to="link.to"
          class="navbar__link"
          @click="mobileOpen = false"
        >
          {{ link.label }}
        </router-link>
        <router-link to="/kontakt" class="navbar__cta" @click="mobileOpen = false">
          Termin vereinbaren
        </router-link>
      </nav>
    </div>
  </header>
</template>

<style scoped>
.navbar {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 1000;
  padding: 1.25rem 0;
  transition: all 0.4s var(--ease-out-expo);
}

.navbar.scrolled {
  padding: 0.6rem 0;
  background: rgba(255, 255, 255, 0.88);
  backdrop-filter: blur(20px) saturate(180%);
  -webkit-backdrop-filter: blur(20px) saturate(180%);
  border-bottom: 1px solid rgba(0, 0, 0, 0.06);
  box-shadow: 0 1px 30px rgba(0, 0, 0, 0.06);
}

.navbar__inner {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.navbar__brand {
  display: flex;
  flex-direction: column;
  gap: 0;
  line-height: 1.1;
  z-index: 10;
}

.brand-name {
  font-family: var(--font-display);
  font-size: 1.35rem;
  font-weight: 600;
  color: var(--white);
  transition: color 0.4s ease;
}

.brand-title {
  font-size: 0.7rem;
  font-weight: 400;
  letter-spacing: 0.15em;
  text-transform: uppercase;
  color: rgba(255, 255, 255, 0.7);
  transition: color 0.4s ease;
}

.scrolled .brand-name {
  color: var(--gray-900);
}

.scrolled .brand-title {
  color: var(--teal);
}

.navbar__nav {
  display: flex;
  align-items: center;
  gap: 2rem;
}

.navbar__link {
  font-size: 0.875rem;
  font-weight: 500;
  color: rgba(255, 255, 255, 0.85);
  letter-spacing: 0.02em;
  position: relative;
  transition: color 0.3s ease;
}

.navbar__link::after {
  content: '';
  position: absolute;
  bottom: -4px;
  left: 0;
  width: 0;
  height: 2px;
  background: var(--teal);
  transition: width 0.3s var(--ease-out-expo);
}

.navbar__link:hover::after,
.navbar__link.router-link-active::after {
  width: 100%;
}

.scrolled .navbar__link {
  color: var(--gray-600);
}

.scrolled .navbar__link:hover,
.scrolled .navbar__link.router-link-active {
  color: var(--gray-900);
}

.navbar__cta {
  font-size: 0.8rem;
  font-weight: 600;
  letter-spacing: 0.03em;
  padding: 0.6rem 1.5rem;
  border-radius: 100px;
  background: var(--teal);
  color: var(--white);
  transition: all 0.3s ease;
}

.navbar__cta:hover {
  background: var(--teal-dark);
  transform: translateY(-1px);
  box-shadow: 0 4px 20px var(--teal-glow);
}

/* Mobile toggle */
.navbar__toggle {
  display: none;
  flex-direction: column;
  gap: 5px;
  z-index: 10;
  padding: 4px;
}

.navbar__toggle span {
  display: block;
  width: 24px;
  height: 2px;
  background: var(--white);
  border-radius: 2px;
  transition: all 0.3s ease;
}

.scrolled .navbar__toggle span {
  background: var(--gray-800);
}

.navbar__toggle.active span:nth-child(1) {
  transform: rotate(45deg) translate(5px, 5px);
}

.navbar__toggle.active span:nth-child(2) {
  opacity: 0;
}

.navbar__toggle.active span:nth-child(3) {
  transform: rotate(-45deg) translate(5px, -5px);
}

@media (max-width: 768px) {
  .navbar__toggle {
    display: flex;
  }

  .navbar__nav {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    flex-direction: column;
    justify-content: center;
    gap: 2rem;
    background: rgba(12, 20, 21, 0.97);
    backdrop-filter: blur(20px);
    opacity: 0;
    pointer-events: none;
    transition: opacity 0.3s ease;
  }

  .navbar__nav.open {
    opacity: 1;
    pointer-events: all;
  }

  .navbar__nav .navbar__link {
    font-size: 1.5rem;
    color: var(--white);
  }

  .mobile-open .navbar__toggle span {
    background: var(--white);
  }

  .mobile-open .brand-name {
    color: var(--white);
  }

  .mobile-open .brand-title {
    color: rgba(255, 255, 255, 0.7);
  }
}
</style>
