<script setup lang="ts">
const services = [
  {
    icon: '/images/icon-gespraech.png',
    title: 'Psychologische Beratung',
    desc: 'Individuelle Beratung bei beruflicher Neuorientierung, Coaching für Führungskräfte und Mediation zur Konfliktlösung.',
    link: '/leistungen#beratung',
  },
  {
    icon: '/images/icon-medaille.png',
    title: 'Sprechstunde Psyche',
    desc: 'Unterstützung bei Stress, Burnout, Konflikten am Arbeitsplatz, Depression, Ängsten und Beziehungsproblemen.',
    link: '/leistungen#sprechstunde',
  },
  {
    icon: '/images/icon-team.png',
    title: 'Schulungen & Seminare',
    desc: 'Teambuilding, Kommunikation und praxisorientiertes Training in Kleingruppen. Maßgeschneiderte Weiterbildung.',
    link: '/leistungen#schulungen',
  },
]
</script>

<template>
  <section class="services">
    <div class="container">
      <div class="services__header reveal">
        <span class="services__label">Leistungen</span>
        <h2 class="services__title">
          Ganzheitliche psychologische<br />
          <em>Unterstützung</em> für Sie
        </h2>
      </div>

      <div class="services__grid">
        <router-link
          v-for="(service, i) in services"
          :key="service.title"
          :to="service.link"
          class="service-card reveal"
          :class="`reveal-delay-${i + 1}`"
        >
          <div class="service-card__icon">
            <img :src="service.icon" :alt="service.title" />
          </div>
          <h3 class="service-card__title">{{ service.title }}</h3>
          <p class="service-card__desc">{{ service.desc }}</p>
          <span class="service-card__arrow">
            <svg width="20" height="20" viewBox="0 0 20 20" fill="none">
              <path d="M5 10h10M11 6l4 4-4 4" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
            </svg>
          </span>
        </router-link>
      </div>
    </div>
  </section>
</template>

<style scoped>
.services {
  padding: var(--section-padding) 0;
  background: var(--white);
}

.services__header {
  text-align: center;
  margin-bottom: 4rem;
}

.services__label {
  display: inline-block;
  font-size: 0.75rem;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.15em;
  color: var(--teal);
  margin-bottom: 1rem;
}

.services__title {
  font-family: var(--font-display);
  font-size: clamp(1.75rem, 4vw, 2.75rem);
  font-weight: 600;
  line-height: 1.2;
  color: var(--gray-900);
}

.services__title em {
  font-style: italic;
  color: var(--teal);
}

.services__grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 2rem;
}

.service-card {
  position: relative;
  padding: 2.5rem 2rem;
  border-radius: 20px;
  background: var(--off-white);
  border: 1px solid var(--gray-100);
  transition: all 0.4s var(--ease-out-expo);
  display: flex;
  flex-direction: column;
  overflow: hidden;
}

.service-card::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 3px;
  background: var(--gradient-teal);
  opacity: 0;
  transition: opacity 0.4s ease;
}

.service-card:hover {
  transform: translateY(-6px);
  box-shadow: 0 20px 60px rgba(0,0,0,0.08);
  border-color: transparent;
}

.service-card:hover::before {
  opacity: 1;
}

.service-card__icon {
  width: 56px;
  height: 56px;
  border-radius: 14px;
  background: var(--white);
  display: flex;
  align-items: center;
  justify-content: center;
  margin-bottom: 1.5rem;
  box-shadow: 0 4px 12px rgba(0,0,0,0.04);
  transition: all 0.4s ease;
}

.service-card:hover .service-card__icon {
  background: var(--teal);
  box-shadow: 0 4px 20px var(--teal-glow);
}

.service-card__icon img {
  width: 28px;
  height: 28px;
  transition: filter 0.4s ease;
}

.service-card:hover .service-card__icon img {
  filter: brightness(0) invert(1);
}

.service-card__title {
  font-family: var(--font-display);
  font-size: 1.25rem;
  font-weight: 600;
  color: var(--gray-900);
  margin-bottom: 0.75rem;
}

.service-card__desc {
  font-size: 0.9rem;
  color: var(--gray-600);
  line-height: 1.6;
  flex: 1;
}

.service-card__arrow {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  width: 36px;
  height: 36px;
  border-radius: 50%;
  background: var(--gray-50);
  color: var(--gray-400);
  margin-top: 1.5rem;
  transition: all 0.3s ease;
}

.service-card:hover .service-card__arrow {
  background: var(--teal);
  color: var(--white);
  transform: translateX(4px);
}

@media (max-width: 768px) {
  .services__grid {
    grid-template-columns: 1fr;
    gap: 1.25rem;
  }
}
</style>
