<script setup lang="ts">
import { useReveal } from '../composables/useReveal'

useReveal()

const base = import.meta.env.BASE_URL

const beratungItems = [
  { icon: `${base}images/icon-neuorientierung.png`, title: 'Berufliche Neuorientierung', desc: 'Begleitung bei beruflichen Veränderungen, Standortbestimmung und Entwicklung neuer Perspektiven.' },
  { icon: `${base}images/icon-fuehrungskraefte.png`, title: 'Coaching für Führungskräfte', desc: 'Stärkung Ihrer Führungskompetenzen, Entscheidungsfindung und persönlichen Weiterentwicklung.' },
  { icon: `${base}images/icon-mediation.png`, title: 'Mediation zur Konfliktlösung', desc: 'Professionelle Vermittlung bei Konflikten im beruflichen und privaten Umfeld.' },
]

const sprechstundeTopics = [
  'Stress & Burnout',
  'Konflikte am Arbeitsplatz',
  'Depression & Ängste',
  'Beziehungsprobleme',
  'Berufliche Entwicklung',
  'Persönliche Krisen',
]

const seminarTopics = [
  'Resilienzkompass',
  'Life-Balance',
  'Konfliktmanagement',
  'Kommunikation',
  'Stressmanagement',
  'Führungskompetenz',
  'Betriebliche Gesundheit',
  'Suchtprävention',
  'Arbeitssicherheit',
]
</script>

<template>
  <main class="leistungen">
    <!-- Page hero -->
    <section class="page-hero">
      <div class="page-hero__bg">
        <img :src="`${base}images/beratung.jpg`" alt="" />
        <div class="page-hero__overlay"></div>
      </div>
      <div class="container page-hero__content">
        <span class="page-hero__label">Leistungen</span>
        <h1 class="page-hero__title">
          Psychologische<br /><em>Expertise</em>
        </h1>
        <p class="page-hero__desc">
          Individuelle Beratung, Seminare und Schulungen – angepasst an Ihre Bedürfnisse.
        </p>
      </div>
    </section>

    <!-- Beratung -->
    <section id="beratung" class="section">
      <div class="container">
        <div class="section__header reveal">
          <span class="section__label">01</span>
          <h2 class="section__title">Psychologische Beratung</h2>
          <p class="section__desc">
            Systemische Beratung mit dem SEELE-Ansatz: Systemisch, Einfühlsam, Emotional, Lösungsorientiert, Empathisch.
          </p>
        </div>

        <div class="beratung-grid">
          <div
            v-for="(item, i) in beratungItems"
            :key="item.title"
            class="beratung-card reveal"
            :class="`reveal-delay-${i + 1}`"
          >
            <div class="beratung-card__icon">
              <img :src="item.icon" :alt="item.title" />
            </div>
            <h3>{{ item.title }}</h3>
            <p>{{ item.desc }}</p>
          </div>
        </div>
      </div>
    </section>

    <!-- Sprechstunde -->
    <section id="sprechstunde" class="section section--dark">
      <div class="container">
        <div class="sprechstunde-layout">
          <div class="sprechstunde-left reveal">
            <span class="section__label section__label--light">02</span>
            <h2 class="section__title section__title--light">Sprechstunde Psyche</h2>
            <p class="section__desc section__desc--light">
              Professionelle Unterstützung bei psychischen Belastungen. In einem geschützten Rahmen
              sprechen wir über das, was Sie bewegt.
            </p>
          </div>
          <div class="sprechstunde-right">
            <div
              v-for="(topic, i) in sprechstundeTopics"
              :key="topic"
              class="topic-chip reveal"
              :class="`reveal-delay-${(i % 4) + 1}`"
            >
              {{ topic }}
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Schulungen -->
    <section id="schulungen" class="section">
      <div class="container">
        <div class="section__header reveal">
          <span class="section__label">03</span>
          <h2 class="section__title">Schulungen</h2>
          <p class="section__desc">
            Teambuilding, Kommunikation und praxisorientiertes Training in Kleingruppen.
          </p>
        </div>

        <div class="schulungen-visual reveal reveal-delay-1">
          <img :src="`${base}images/schulungen.jpg`" alt="Schulungen" class="schulungen-img" />
          <div class="schulungen-overlay">
            <div class="schulungen-stat">
              <span class="schulungen-stat__number">15+</span>
              <span class="schulungen-stat__label">Jahre Erfahrung</span>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Seminare -->
    <section id="seminare" class="section section--gray">
      <div class="container">
        <div class="section__header reveal">
          <span class="section__label">04</span>
          <h2 class="section__title">Seminare</h2>
          <p class="section__desc">
            Maßgeschneiderte Seminarangebote für Unternehmen und Einzelpersonen.
          </p>
        </div>

        <div class="seminare-grid">
          <div
            v-for="(topic, i) in seminarTopics"
            :key="topic"
            class="seminar-card reveal"
            :class="`reveal-delay-${(i % 4) + 1}`"
          >
            <span class="seminar-card__num">{{ String(i + 1).padStart(2, '0') }}</span>
            <h3>{{ topic }}</h3>
          </div>
        </div>
      </div>
    </section>
  </main>
</template>

<style scoped>
/* Page hero */
.page-hero {
  position: relative;
  min-height: 60vh;
  display: flex;
  align-items: flex-end;
  padding-bottom: 4rem;
  overflow: hidden;
}

.page-hero__bg {
  position: absolute;
  inset: 0;
}

.page-hero__bg img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.page-hero__overlay {
  position: absolute;
  inset: 0;
  background: linear-gradient(180deg, rgba(12,20,21,0.3) 0%, rgba(12,20,21,0.75) 100%);
}

.page-hero__content {
  position: relative;
  z-index: 2;
  padding-top: 8rem;
}

.page-hero__label {
  display: inline-block;
  font-size: 0.75rem;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.15em;
  color: var(--teal-light);
  margin-bottom: 1rem;
}

.page-hero__title {
  font-family: var(--font-display);
  font-size: clamp(2.5rem, 6vw, 4rem);
  font-weight: 700;
  line-height: 1.1;
  color: var(--white);
}

.page-hero__title em {
  font-style: italic;
  color: var(--teal-light);
}

.page-hero__desc {
  margin-top: 1rem;
  font-size: 1.1rem;
  color: rgba(255,255,255,0.6);
  max-width: 500px;
}

/* Sections */
.section {
  padding: var(--section-padding) 0;
}

.section--dark {
  background: var(--gray-900);
}

.section--gray {
  background: var(--gray-50);
}

.section__header {
  text-align: center;
  margin-bottom: 3.5rem;
  max-width: 600px;
  margin-left: auto;
  margin-right: auto;
}

.section__label {
  display: inline-block;
  font-size: 0.8rem;
  font-weight: 700;
  font-family: var(--font-display);
  color: var(--teal);
  margin-bottom: 0.75rem;
}

.section__label--light {
  color: var(--teal-light);
}

.section__title {
  font-family: var(--font-display);
  font-size: clamp(1.75rem, 4vw, 2.5rem);
  font-weight: 600;
  color: var(--gray-900);
}

.section__title--light {
  color: var(--white);
}

.section__desc {
  margin-top: 0.75rem;
  color: var(--gray-600);
  font-size: 1rem;
  line-height: 1.7;
}

.section__desc--light {
  color: rgba(255,255,255,0.5);
}

/* Beratung */
.beratung-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 2rem;
}

.beratung-card {
  text-align: center;
  padding: 2.5rem 2rem;
  border-radius: 20px;
  background: var(--white);
  border: 1px solid var(--gray-100);
  transition: all 0.4s var(--ease-out-expo);
}

.beratung-card:hover {
  transform: translateY(-4px);
  box-shadow: 0 16px 48px rgba(0,0,0,0.08);
}

.beratung-card__icon {
  width: 64px;
  height: 64px;
  margin: 0 auto 1.5rem;
  border-radius: 16px;
  background: var(--gray-50);
  display: flex;
  align-items: center;
  justify-content: center;
  transition: all 0.4s ease;
}

.beratung-card:hover .beratung-card__icon {
  background: var(--teal);
}

.beratung-card__icon img {
  width: 32px;
  height: 32px;
  transition: filter 0.4s ease;
}

.beratung-card:hover .beratung-card__icon img {
  filter: brightness(0) invert(1);
}

.beratung-card h3 {
  font-family: var(--font-display);
  font-size: 1.15rem;
  font-weight: 600;
  color: var(--gray-900);
  margin-bottom: 0.5rem;
}

.beratung-card p {
  font-size: 0.875rem;
  color: var(--gray-600);
  line-height: 1.6;
}

/* Sprechstunde */
.sprechstunde-layout {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 4rem;
  align-items: center;
}

.sprechstunde-right {
  display: flex;
  flex-wrap: wrap;
  gap: 0.75rem;
}

.topic-chip {
  padding: 0.7rem 1.5rem;
  border-radius: 100px;
  background: rgba(255,255,255,0.06);
  border: 1px solid rgba(255,255,255,0.1);
  color: rgba(255,255,255,0.8);
  font-size: 0.9rem;
  font-weight: 500;
  transition: all 0.3s ease;
}

.topic-chip:hover {
  background: var(--teal);
  border-color: var(--teal);
  color: var(--white);
  transform: translateY(-2px);
}

/* Schulungen */
.schulungen-visual {
  position: relative;
  border-radius: 20px;
  overflow: hidden;
  max-height: 400px;
}

.schulungen-img {
  width: 100%;
  height: 400px;
  object-fit: cover;
}

.schulungen-overlay {
  position: absolute;
  inset: 0;
  background: linear-gradient(135deg, rgba(42,181,178,0.8) 0%, rgba(12,20,21,0.4) 100%);
  display: flex;
  align-items: center;
  justify-content: center;
}

.schulungen-stat {
  text-align: center;
  color: var(--white);
}

.schulungen-stat__number {
  display: block;
  font-family: var(--font-display);
  font-size: 5rem;
  font-weight: 700;
  line-height: 1;
}

.schulungen-stat__label {
  display: block;
  margin-top: 0.5rem;
  font-size: 1.1rem;
  font-weight: 400;
  opacity: 0.8;
}

/* Seminare */
.seminare-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 1rem;
}

.seminar-card {
  padding: 1.75rem;
  border-radius: 16px;
  background: var(--white);
  border: 1px solid var(--gray-100);
  transition: all 0.3s var(--ease-out-expo);
}

.seminar-card:hover {
  border-color: var(--teal);
  transform: translateY(-2px);
  box-shadow: 0 8px 24px rgba(42,181,178,0.1);
}

.seminar-card__num {
  font-family: var(--font-display);
  font-size: 0.8rem;
  font-weight: 700;
  color: var(--teal);
}

.seminar-card h3 {
  font-size: 1rem;
  font-weight: 600;
  color: var(--gray-900);
  margin-top: 0.5rem;
}

@media (max-width: 768px) {
  .beratung-grid,
  .seminare-grid {
    grid-template-columns: 1fr;
  }

  .sprechstunde-layout {
    grid-template-columns: 1fr;
    gap: 2rem;
  }
}
</style>
