<script setup lang="ts">
import { useReveal } from '../composables/useReveal'

useReveal()

const contactInfo = [
  { icon: 'phone', label: 'Telefon', value: '06151 317027', href: 'tel:06151317027' },
  { icon: 'mobile', label: 'Mobil', value: '0175 5468075', href: 'tel:01755468075' },
  { icon: 'mail', label: 'E-Mail', value: 'info@psychologin-angelaeinicke.de', href: 'mailto:info@psychologin-angelaeinicke.de' },
  { icon: 'pin', label: 'Adresse', value: 'Erbacher Str. 109, 64287 Darmstadt', href: 'https://maps.google.com/?q=Erbacher+Str.+109,+64287+Darmstadt' },
]
</script>

<template>
  <main class="kontakt">
    <section class="kontakt-hero">
      <div class="container">
        <div class="kontakt-hero__content">
          <span class="kontakt-hero__label">Kontakt</span>
          <h1 class="kontakt-hero__title">
            Lassen Sie uns<br /><em>sprechen</em>
          </h1>
          <p class="kontakt-hero__desc">
            Vereinbaren Sie ein unverbindliches Erstgespräch.<br />
            Ich freue mich darauf, Sie kennenzulernen.
          </p>
        </div>
      </div>
    </section>

    <section class="kontakt-body">
      <div class="container">
        <div class="kontakt-layout">
          <!-- Contact info -->
          <div class="kontakt-info">
            <div
              v-for="(item, i) in contactInfo"
              :key="item.label"
              class="contact-item reveal"
              :class="`reveal-delay-${i + 1}`"
            >
              <div class="contact-item__icon">
                <img :src="`/images/icon-${item.icon}.svg`" :alt="item.label" />
              </div>
              <div class="contact-item__body">
                <span class="contact-item__label">{{ item.label }}</span>
                <a :href="item.href" target="_blank" rel="noopener" class="contact-item__value">
                  {{ item.value }}
                </a>
              </div>
            </div>

            <!-- Transport -->
            <div class="transport reveal reveal-delay-4">
              <div class="contact-item__icon">
                <img src="/images/icon-bus.svg" alt="Bus" />
              </div>
              <div class="contact-item__body">
                <span class="contact-item__label">Öffentliche Verkehrsmittel</span>
                <span class="contact-item__value">Bushaltestelle Rosenhöhe (Linien RH, MO1, GB)</span>
              </div>
            </div>
          </div>

          <!-- Contact form -->
          <div class="kontakt-form-wrap reveal reveal-delay-2">
            <h2>Nachricht senden</h2>
            <form class="kontakt-form" @submit.prevent>
              <div class="form-group">
                <label for="name">Name</label>
                <input id="name" type="text" placeholder="Ihr vollständiger Name" />
              </div>
              <div class="form-group">
                <label for="email">E-Mail</label>
                <input id="email" type="email" placeholder="ihre@email.de" />
              </div>
              <div class="form-group">
                <label for="subject">Betreff</label>
                <input id="subject" type="text" placeholder="Worum geht es?" />
              </div>
              <div class="form-group">
                <label for="message">Nachricht</label>
                <textarea id="message" rows="5" placeholder="Ihre Nachricht an mich..."></textarea>
              </div>
              <button type="submit" class="form-submit">
                Nachricht senden
                <svg width="16" height="16" viewBox="0 0 16 16" fill="none">
                  <path d="M3 8h10M9 4l4 4-4 4" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
                </svg>
              </button>
            </form>
          </div>
        </div>
      </div>
    </section>
  </main>
</template>

<style scoped>
.kontakt-hero {
  padding-top: 10rem;
  padding-bottom: 4rem;
  background: var(--gray-900);
  color: var(--white);
}

.kontakt-hero__label {
  display: inline-block;
  font-size: 0.75rem;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.15em;
  color: var(--teal-light);
  margin-bottom: 1rem;
}

.kontakt-hero__title {
  font-family: var(--font-display);
  font-size: clamp(2.5rem, 6vw, 4rem);
  font-weight: 700;
  line-height: 1.1;
}

.kontakt-hero__title em {
  font-style: italic;
  color: var(--teal-light);
}

.kontakt-hero__desc {
  margin-top: 1.25rem;
  font-size: 1.1rem;
  color: rgba(255,255,255,0.5);
  line-height: 1.7;
}

/* Body */
.kontakt-body {
  padding: var(--section-padding) 0;
}

.kontakt-layout {
  display: grid;
  grid-template-columns: 1fr 1.2fr;
  gap: 4rem;
  align-items: start;
}

/* Info */
.kontakt-info {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.contact-item,
.transport {
  display: flex;
  align-items: flex-start;
  gap: 1rem;
  padding: 1.25rem;
  border-radius: 16px;
  background: var(--gray-50);
  border: 1px solid var(--gray-100);
  transition: all 0.3s ease;
}

.contact-item:hover {
  border-color: var(--teal-lighter);
  background: var(--white);
  box-shadow: 0 4px 16px rgba(42,181,178,0.08);
}

.contact-item__icon {
  width: 44px;
  height: 44px;
  border-radius: 12px;
  background: var(--white);
  display: flex;
  align-items: center;
  justify-content: center;
  flex-shrink: 0;
  box-shadow: 0 2px 8px rgba(0,0,0,0.04);
}

.contact-item__icon img {
  width: 20px;
  height: 20px;
}

.contact-item__label {
  display: block;
  font-size: 0.75rem;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.1em;
  color: var(--gray-400);
  margin-bottom: 0.15rem;
}

.contact-item__value {
  font-size: 0.95rem;
  color: var(--gray-800);
  font-weight: 500;
}

a.contact-item__value:hover {
  color: var(--teal);
}

/* Form */
.kontakt-form-wrap {
  padding: 2.5rem;
  border-radius: 24px;
  background: var(--white);
  border: 1px solid var(--gray-100);
  box-shadow: 0 8px 40px rgba(0,0,0,0.04);
}

.kontakt-form-wrap h2 {
  font-family: var(--font-display);
  font-size: 1.5rem;
  font-weight: 600;
  color: var(--gray-900);
  margin-bottom: 2rem;
}

.kontakt-form {
  display: flex;
  flex-direction: column;
  gap: 1.25rem;
}

.form-group label {
  display: block;
  font-size: 0.8rem;
  font-weight: 600;
  color: var(--gray-600);
  margin-bottom: 0.4rem;
  letter-spacing: 0.02em;
}

.form-group input,
.form-group textarea {
  width: 100%;
  padding: 0.8rem 1rem;
  border: 1px solid var(--gray-100);
  border-radius: 12px;
  font-family: var(--font-body);
  font-size: 0.9rem;
  color: var(--gray-800);
  background: var(--gray-50);
  transition: all 0.3s ease;
  outline: none;
}

.form-group input:focus,
.form-group textarea:focus {
  border-color: var(--teal);
  background: var(--white);
  box-shadow: 0 0 0 3px var(--teal-glow);
}

.form-group textarea {
  resize: vertical;
  min-height: 120px;
}

.form-submit {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  padding: 0.85rem 2rem;
  border-radius: 100px;
  background: var(--teal);
  color: var(--white);
  font-size: 0.9rem;
  font-weight: 600;
  transition: all 0.3s var(--ease-out-expo);
  align-self: flex-start;
}

.form-submit:hover {
  background: var(--teal-dark);
  transform: translateY(-2px);
  box-shadow: 0 8px 30px var(--teal-glow);
}

@media (max-width: 768px) {
  .kontakt-layout {
    grid-template-columns: 1fr;
    gap: 2.5rem;
  }
}
</style>
