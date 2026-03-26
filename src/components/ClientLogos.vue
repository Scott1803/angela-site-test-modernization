<script setup lang="ts">
const logos = [
  { src: '/images/logo-amazon.png', alt: 'Amazon' },
  { src: '/images/logo-db.png', alt: 'Deutsche Bahn' },
  { src: '/images/logo-daimler.png', alt: 'Daimler' },
  { src: '/images/logo-galeria.png', alt: 'Galeria' },
  { src: '/images/logo-ivp.png', alt: 'IVP' },
  { src: '/images/logo-ifb.png', alt: 'ifb' },
  { src: '/images/logo-insite.png', alt: 'INSITE' },
  { src: '/images/logo-waf.png', alt: 'WAF' },
  { src: '/images/logo-ikae.png', alt: 'IKAE' },
]
</script>

<template>
  <section class="clients">
    <div class="container">
      <div class="clients__header reveal">
        <span class="clients__label">Vertrauen</span>
        <h2 class="clients__title">Referenzen & Kooperationen</h2>
      </div>

      <div class="clients__track reveal reveal-delay-2">
        <div class="clients__scroll">
          <div v-for="logo in logos" :key="logo.alt" class="clients__logo">
            <img :src="logo.src" :alt="logo.alt" />
          </div>
          <!-- Duplicate for infinite scroll -->
          <div v-for="logo in logos" :key="logo.alt + '-dup'" class="clients__logo">
            <img :src="logo.src" :alt="logo.alt" />
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.clients {
  padding: var(--section-padding) 0;
  background: var(--white);
  overflow: hidden;
}

.clients__header {
  text-align: center;
  margin-bottom: 3rem;
}

.clients__label {
  display: inline-block;
  font-size: 0.75rem;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.15em;
  color: var(--teal);
  margin-bottom: 0.75rem;
}

.clients__title {
  font-family: var(--font-display);
  font-size: clamp(1.5rem, 3vw, 2rem);
  font-weight: 600;
  color: var(--gray-900);
}

.clients__track {
  position: relative;
  mask-image: linear-gradient(90deg, transparent, black 10%, black 90%, transparent);
  -webkit-mask-image: linear-gradient(90deg, transparent, black 10%, black 90%, transparent);
}

.clients__scroll {
  display: flex;
  gap: 3rem;
  animation: scrollLogos 30s linear infinite;
  width: max-content;
}

.clients__logo {
  flex-shrink: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 48px;
  opacity: 0.4;
  filter: grayscale(100%);
  transition: all 0.4s ease;
}

.clients__logo:hover {
  opacity: 1;
  filter: grayscale(0%);
}

.clients__logo img {
  max-height: 100%;
  max-width: 120px;
  object-fit: contain;
}

@keyframes scrollLogos {
  0% { transform: translateX(0); }
  100% { transform: translateX(calc(-50% - 1.5rem)); }
}
</style>
