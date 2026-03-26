<script setup lang="ts">
</script>

<template>
  <section class="cta">
    <div class="container">
      <div class="cta__card reveal">
        <div class="cta__bg"></div>
        <div class="cta__content">
          <h2 class="cta__title">
            Bereit für den<br />
            <em>ersten Schritt?</em>
          </h2>
          <p class="cta__desc">
            Vereinbaren Sie ein unverbindliches Erstgespräch. Gemeinsam finden wir
            den richtigen Weg für Sie.
          </p>
          <div class="cta__actions">
            <router-link to="/kontakt" class="cta__btn cta__btn--primary">
              Jetzt Kontakt aufnehmen
              <svg width="16" height="16" viewBox="0 0 16 16" fill="none">
                <path d="M3 8h10M9 4l4 4-4 4" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
              </svg>
            </router-link>
            <a href="tel:06151317027" class="cta__btn cta__btn--outline">
              06151 317027
            </a>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.cta {
  padding: 0 0 var(--section-padding);
  background: var(--white);
}

.cta__card {
  position: relative;
  border-radius: 24px;
  overflow: hidden;
  padding: clamp(3rem, 6vw, 5rem);
}

.cta__bg {
  position: absolute;
  inset: 0;
  background:
    radial-gradient(ellipse at 80% 20%, rgba(42,181,178,0.15) 0%, transparent 50%),
    radial-gradient(ellipse at 20% 80%, rgba(42,181,178,0.1) 0%, transparent 50%),
    var(--gray-900);
}

.cta__content {
  position: relative;
  z-index: 1;
  max-width: 550px;
}

.cta__title {
  font-family: var(--font-display);
  font-size: clamp(2rem, 4vw, 3rem);
  font-weight: 700;
  line-height: 1.15;
  color: var(--white);
}

.cta__title em {
  font-style: italic;
  color: var(--teal-light);
}

.cta__desc {
  margin-top: 1.25rem;
  font-size: 1.05rem;
  line-height: 1.7;
  color: rgba(255,255,255,0.6);
}

.cta__actions {
  display: flex;
  gap: 1rem;
  margin-top: 2rem;
  flex-wrap: wrap;
}

.cta__btn {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  padding: 0.85rem 2rem;
  border-radius: 100px;
  font-size: 0.9rem;
  font-weight: 600;
  transition: all 0.3s var(--ease-out-expo);
}

.cta__btn--primary {
  background: var(--teal);
  color: var(--white);
}

.cta__btn--primary:hover {
  background: var(--teal-light);
  transform: translateY(-2px);
  box-shadow: 0 8px 30px var(--teal-glow);
}

.cta__btn--outline {
  border: 1px solid rgba(255,255,255,0.2);
  color: var(--white);
}

.cta__btn--outline:hover {
  background: rgba(255,255,255,0.1);
  transform: translateY(-2px);
}
</style>
