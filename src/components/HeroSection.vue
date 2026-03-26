<script setup lang="ts">
import { ref, onMounted } from 'vue'

const heroLoaded = ref(false)

onMounted(() => {
  requestAnimationFrame(() => {
    heroLoaded.value = true
  })
})
</script>

<template>
  <section class="hero">
    <div class="hero__bg">
      <img src="/images/hero-bg.jpg" alt="" class="hero__img" />
      <div class="hero__overlay"></div>
    </div>

    <div class="hero__content container" :class="{ loaded: heroLoaded }">
      <div class="hero__badge">
        <span class="hero__badge-dot"></span>
        Diplom-Psychologin in Darmstadt
      </div>

      <h1 class="hero__title">
        Ich erfülle Ihre<br />
        <em>Erwartungen</em> an<br />
        die Psychologin
      </h1>

      <p class="hero__subtitle">
        Ich liebe Menschen in Ihrer Einzigartigkeit.
      </p>

      <div class="hero__actions">
        <router-link to="/kontakt" class="hero__btn hero__btn--primary">
          Termin vereinbaren
          <svg width="16" height="16" viewBox="0 0 16 16" fill="none">
            <path d="M3 8h10M9 4l4 4-4 4" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
          </svg>
        </router-link>
        <router-link to="/leistungen" class="hero__btn hero__btn--glass">
          Leistungen entdecken
        </router-link>
      </div>

      <div class="hero__scroll-hint">
        <div class="hero__scroll-line"></div>
      </div>
    </div>

    <!-- Floating glass cards -->
    <div class="hero__float hero__float--1" :class="{ loaded: heroLoaded }">
      <img src="/images/icon-neuorientierung.png" alt="" />
      <span>Beratung</span>
    </div>
    <div class="hero__float hero__float--2" :class="{ loaded: heroLoaded }">
      <img src="/images/icon-mediation.png" alt="" />
      <span>Mediation</span>
    </div>
  </section>
</template>

<style scoped>
.hero {
  position: relative;
  min-height: 100vh;
  display: flex;
  align-items: center;
  overflow: hidden;
}

.hero__bg {
  position: absolute;
  inset: 0;
  z-index: 0;
}

.hero__img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: center 30%;
  scale: 1.05;
  animation: heroZoom 20s ease-in-out infinite alternate;
}

@keyframes heroZoom {
  0% { scale: 1.05; object-position: center 30%; }
  100% { scale: 1.12; object-position: center 35%; }
}

.hero__overlay {
  position: absolute;
  inset: 0;
  background:
    linear-gradient(180deg, rgba(12,20,21,0.2) 0%, rgba(12,20,21,0.55) 70%, rgba(12,20,21,0.85) 100%),
    linear-gradient(135deg, rgba(42,181,178,0.08) 0%, transparent 50%);
}

.hero__content {
  position: relative;
  z-index: 2;
  padding-top: 10rem;
  padding-bottom: 4rem;
}

/* Staggered entrance */
.hero__content > * {
  opacity: 0;
  transform: translateY(30px);
  transition: opacity 0.8s var(--ease-out-expo), transform 0.8s var(--ease-out-expo);
}

.hero__content.loaded > *:nth-child(1) { opacity: 1; transform: translateY(0); transition-delay: 0.2s; }
.hero__content.loaded > *:nth-child(2) { opacity: 1; transform: translateY(0); transition-delay: 0.4s; }
.hero__content.loaded > *:nth-child(3) { opacity: 1; transform: translateY(0); transition-delay: 0.6s; }
.hero__content.loaded > *:nth-child(4) { opacity: 1; transform: translateY(0); transition-delay: 0.8s; }
.hero__content.loaded > *:nth-child(5) { opacity: 1; transform: translateY(0); transition-delay: 1s; }

.hero__badge {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  padding: 0.4rem 1rem;
  border-radius: 100px;
  background: rgba(255,255,255,0.1);
  backdrop-filter: blur(10px);
  border: 1px solid rgba(255,255,255,0.15);
  font-size: 0.8rem;
  font-weight: 500;
  color: rgba(255,255,255,0.9);
  letter-spacing: 0.04em;
}

.hero__badge-dot {
  width: 6px;
  height: 6px;
  border-radius: 50%;
  background: var(--teal);
  animation: pulse 2s ease-in-out infinite;
}

@keyframes pulse {
  0%, 100% { opacity: 1; scale: 1; }
  50% { opacity: 0.6; scale: 1.3; }
}

.hero__title {
  font-family: var(--font-display);
  font-size: clamp(2.5rem, 6vw, 4.5rem);
  font-weight: 700;
  line-height: 1.1;
  color: var(--white);
  margin-top: 1.5rem;
  letter-spacing: -0.02em;
}

.hero__title em {
  font-style: italic;
  color: var(--teal-light);
}

.hero__subtitle {
  font-size: clamp(1rem, 2vw, 1.25rem);
  color: rgba(255,255,255,0.7);
  margin-top: 1.25rem;
  font-weight: 300;
  max-width: 500px;
}

.hero__actions {
  display: flex;
  gap: 1rem;
  margin-top: 2.5rem;
  flex-wrap: wrap;
}

.hero__btn {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  padding: 0.85rem 2rem;
  border-radius: 100px;
  font-size: 0.9rem;
  font-weight: 600;
  letter-spacing: 0.02em;
  transition: all 0.3s var(--ease-out-expo);
}

.hero__btn--primary {
  background: var(--teal);
  color: var(--white);
}

.hero__btn--primary:hover {
  background: var(--teal-dark);
  transform: translateY(-2px);
  box-shadow: 0 8px 30px var(--teal-glow);
}

.hero__btn--glass {
  background: rgba(255,255,255,0.1);
  backdrop-filter: blur(10px);
  border: 1px solid rgba(255,255,255,0.2);
  color: var(--white);
}

.hero__btn--glass:hover {
  background: rgba(255,255,255,0.18);
  transform: translateY(-2px);
}

.hero__scroll-hint {
  margin-top: 4rem;
  width: 1px;
  height: 60px;
  background: rgba(255,255,255,0.15);
  position: relative;
  overflow: hidden;
}

.hero__scroll-line {
  width: 100%;
  height: 30px;
  background: var(--teal);
  animation: scrollLine 2s ease-in-out infinite;
}

@keyframes scrollLine {
  0% { transform: translateY(-30px); }
  100% { transform: translateY(60px); }
}

/* Floating glass cards */
.hero__float {
  position: absolute;
  z-index: 3;
  display: flex;
  align-items: center;
  gap: 0.75rem;
  padding: 0.75rem 1.25rem;
  border-radius: 16px;
  background: rgba(255,255,255,0.1);
  backdrop-filter: blur(20px);
  border: 1px solid rgba(255,255,255,0.15);
  color: var(--white);
  font-size: 0.85rem;
  font-weight: 500;
  opacity: 0;
  transition: opacity 1s ease 1.2s, transform 1s var(--ease-out-expo) 1.2s;
  transform: translateY(20px);
}

.hero__float.loaded {
  opacity: 1;
  transform: translateY(0);
}

.hero__float img {
  width: 32px;
  height: 32px;
  filter: brightness(0) invert(1);
}

.hero__float--1 {
  right: 8%;
  top: 35%;
  animation: floatCard1 6s ease-in-out infinite;
  animation-delay: 1.5s;
}

.hero__float--2 {
  right: 12%;
  bottom: 25%;
  animation: floatCard2 7s ease-in-out infinite;
  animation-delay: 2s;
  transition-delay: 1.5s;
}

@keyframes floatCard1 {
  0%, 100% { transform: translateY(0); }
  50% { transform: translateY(-12px); }
}

@keyframes floatCard2 {
  0%, 100% { transform: translateY(0); }
  50% { transform: translateY(10px); }
}

@media (max-width: 768px) {
  .hero__content {
    padding-top: 8rem;
    padding-bottom: 3rem;
  }

  .hero__float {
    display: none;
  }

  .hero__scroll-hint {
    margin-top: 2rem;
  }
}
</style>
