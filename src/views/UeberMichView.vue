<script setup lang="ts">
import { useReveal } from '../composables/useReveal'

useReveal()

const base = import.meta.env.BASE_URL

const qualifications = [
  'Systemische Beraterin',
  'Fachpsychologin für Verkehrspsychologie',
  'Fachkraft für betriebliches Gesundheitsmanagement',
  'Referentin für Erwachsenenbildung',
]
</script>

<template>
  <main class="about">
    <!-- Hero -->
    <section class="about-hero">
      <div class="container">
        <div class="about-hero__layout">
          <div class="about-hero__text">
            <span class="about-hero__label">Über mich</span>
            <h1 class="about-hero__title">
              Angela<br /><em>Einicke</em>
            </h1>
            <p class="about-hero__subtitle">Diplom-Psychologin</p>
          </div>
          <div class="about-hero__image reveal">
            <img :src="`${base}images/portrait.jpg`" alt="Angela Einicke" />
            <div class="about-hero__image-accent"></div>
          </div>
        </div>
      </div>
    </section>

    <!-- Bio -->
    <section class="about-bio">
      <div class="container">
        <div class="about-bio__layout">
          <div class="about-bio__content reveal">
            <h2>
              Ich liebe Menschen in Ihrer <em>Einzigartigkeit</em>
            </h2>
            <p>
              Als Diplom-Psychologin mit langjähriger Erfahrung unterstütze ich
              Menschen und Unternehmen dabei, ihre Herausforderungen zu meistern.
              Mein Ansatz ist systemisch, einfühlsam und immer lösungsorientiert.
            </p>
            <p>
              In meiner Praxis in Darmstadt biete ich Ihnen einen geschützten Raum,
              in dem Sie sich öffnen und neue Wege entdecken können.
            </p>
          </div>

          <div class="about-bio__quals reveal reveal-delay-2">
            <h3>Qualifikationen</h3>
            <ul>
              <li v-for="qual in qualifications" :key="qual">
                <span class="qual-dot"></span>
                {{ qual }}
              </li>
            </ul>
          </div>
        </div>
      </div>
    </section>

    <!-- Values -->
    <section class="about-values">
      <div class="container">
        <div class="values-grid">
          <div class="value-card reveal">
            <span class="value-card__number">01</span>
            <h3>Vertrauen</h3>
            <p>Vertraulichkeit und gegenseitiger Respekt bilden das Fundament meiner Arbeit.</p>
          </div>
          <div class="value-card reveal reveal-delay-1">
            <span class="value-card__number">02</span>
            <h3>Kompetenz</h3>
            <p>Fundierte Ausbildung und stetige Weiterbildung garantieren professionelle Betreuung.</p>
          </div>
          <div class="value-card reveal reveal-delay-2">
            <span class="value-card__number">03</span>
            <h3>Empathie</h3>
            <p>Einfühlsame Begleitung auf Augenhöhe, angepasst an Ihre individuellen Bedürfnisse.</p>
          </div>
        </div>
      </div>
    </section>
  </main>
</template>

<style scoped>
.about-hero {
  padding-top: 10rem;
  padding-bottom: 4rem;
  background: var(--gray-900);
  color: var(--white);
  overflow: hidden;
}

.about-hero__layout {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 4rem;
  align-items: center;
}

.about-hero__label {
  display: inline-block;
  font-size: 0.75rem;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.15em;
  color: var(--teal-light);
  margin-bottom: 1rem;
}

.about-hero__title {
  font-family: var(--font-display);
  font-size: clamp(3rem, 7vw, 5rem);
  font-weight: 700;
  line-height: 1.05;
}

.about-hero__title em {
  font-style: italic;
  color: var(--teal-light);
}

.about-hero__subtitle {
  margin-top: 1rem;
  font-size: 1.1rem;
  color: rgba(255,255,255,0.5);
  letter-spacing: 0.05em;
}

.about-hero__image {
  position: relative;
}

.about-hero__image img {
  width: 100%;
  border-radius: 24px;
  object-fit: cover;
  aspect-ratio: 3/4;
  position: relative;
  z-index: 1;
}

.about-hero__image-accent {
  position: absolute;
  inset: 1rem -1rem -1rem 1rem;
  border-radius: 24px;
  border: 2px solid var(--teal);
  opacity: 0.3;
  z-index: 0;
}

/* Bio */
.about-bio {
  padding: var(--section-padding) 0;
}

.about-bio__layout {
  display: grid;
  grid-template-columns: 1.5fr 1fr;
  gap: 4rem;
  align-items: start;
}

.about-bio__content h2 {
  font-family: var(--font-display);
  font-size: clamp(1.5rem, 3vw, 2.25rem);
  font-weight: 600;
  line-height: 1.3;
  color: var(--gray-900);
  margin-bottom: 1.5rem;
}

.about-bio__content h2 em {
  font-style: italic;
  color: var(--teal);
}

.about-bio__content p {
  font-size: 1rem;
  line-height: 1.8;
  color: var(--gray-600);
  margin-bottom: 1rem;
}

.about-bio__quals h3 {
  font-size: 0.8rem;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.12em;
  color: var(--teal);
  margin-bottom: 1.5rem;
}

.about-bio__quals ul {
  list-style: none;
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.about-bio__quals li {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  font-size: 0.95rem;
  color: var(--gray-800);
}

.qual-dot {
  flex-shrink: 0;
  width: 8px;
  height: 8px;
  border-radius: 50%;
  background: var(--teal);
}

/* Values */
.about-values {
  padding: 0 0 var(--section-padding);
}

.values-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 2rem;
}

.value-card {
  padding: 2.5rem 2rem;
  border-radius: 20px;
  background: var(--gray-50);
  border: 1px solid var(--gray-100);
  transition: all 0.4s var(--ease-out-expo);
}

.value-card:hover {
  transform: translateY(-4px);
  background: var(--white);
  box-shadow: 0 16px 48px rgba(0,0,0,0.06);
}

.value-card__number {
  font-family: var(--font-display);
  font-size: 0.85rem;
  font-weight: 700;
  color: var(--teal);
}

.value-card h3 {
  font-family: var(--font-display);
  font-size: 1.3rem;
  font-weight: 600;
  color: var(--gray-900);
  margin-top: 0.75rem;
  margin-bottom: 0.5rem;
}

.value-card p {
  font-size: 0.9rem;
  color: var(--gray-600);
  line-height: 1.6;
}

@media (max-width: 768px) {
  .about-hero__layout {
    grid-template-columns: 1fr;
    gap: 2rem;
  }

  .about-bio__layout {
    grid-template-columns: 1fr;
    gap: 2rem;
  }

  .values-grid {
    grid-template-columns: 1fr;
  }
}
</style>
