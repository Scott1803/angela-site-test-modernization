<script setup lang="ts">
const letters = [
  { letter: 'S', word: 'Systemisch', desc: 'Ganzheitliche Betrachtung aller Zusammenhänge' },
  { letter: 'E', word: 'Einfühlsam', desc: 'Verständnisvolle Zuwendung in jeder Situation' },
  { letter: 'E', word: 'Emotional', desc: 'Raum für alle Gefühle und Empfindungen' },
  { letter: 'L', word: 'Lösungsorientiert', desc: 'Fokus auf praktische, umsetzbare Wege' },
  { letter: 'E', word: 'Empathisch', desc: 'Tiefes Mitgefühl und echte Anteilnahme' },
]
</script>

<template>
  <section class="seele">
    <div class="container">
      <div class="seele__layout">
        <div class="seele__left reveal">
          <span class="seele__label">Mein Ansatz</span>
          <h2 class="seele__title">
            Der <em>SEELE</em>-Ansatz
          </h2>
          <p class="seele__desc">
            Mein therapeutischer Ansatz verbindet fünf wesentliche Prinzipien
            zu einem ganzheitlichen Beratungskonzept, das Sie in Ihrer
            Einzigartigkeit wahrnimmt und unterstützt.
          </p>
        </div>

        <div class="seele__right">
          <div
            v-for="(item, i) in letters"
            :key="item.word"
            class="seele-card reveal"
            :class="`reveal-delay-${i + 1}`"
          >
            <div class="seele-card__letter">{{ item.letter }}</div>
            <div class="seele-card__body">
              <h3>{{ item.word }}</h3>
              <p>{{ item.desc }}</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.seele {
  padding: var(--section-padding) 0;
  background: var(--gray-900);
  color: var(--white);
  position: relative;
  overflow: hidden;
}

.seele::before {
  content: '';
  position: absolute;
  width: 500px;
  height: 500px;
  border-radius: 50%;
  background: radial-gradient(circle, var(--teal-glow) 0%, transparent 70%);
  top: -100px;
  right: -100px;
  pointer-events: none;
}

.seele__layout {
  display: grid;
  grid-template-columns: 1fr 1.2fr;
  gap: 4rem;
  align-items: start;
}

.seele__left {
  position: sticky;
  top: 8rem;
}

.seele__label {
  display: inline-block;
  font-size: 0.75rem;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.15em;
  color: var(--teal-light);
  margin-bottom: 1rem;
}

.seele__title {
  font-family: var(--font-display);
  font-size: clamp(2rem, 4vw, 3rem);
  font-weight: 700;
  line-height: 1.15;
  margin-bottom: 1.25rem;
}

.seele__title em {
  font-style: normal;
  background: var(--gradient-teal);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.seele__desc {
  font-size: 1rem;
  line-height: 1.7;
  color: rgba(255,255,255,0.6);
}

.seele__right {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.seele-card {
  display: flex;
  align-items: center;
  gap: 1.5rem;
  padding: 1.5rem;
  border-radius: 16px;
  background: rgba(255,255,255,0.04);
  border: 1px solid rgba(255,255,255,0.06);
  transition: all 0.4s var(--ease-out-expo);
}

.seele-card:hover {
  background: rgba(255,255,255,0.08);
  border-color: var(--teal-glow);
  transform: translateX(8px);
}

.seele-card__letter {
  flex-shrink: 0;
  width: 56px;
  height: 56px;
  border-radius: 14px;
  background: var(--gradient-teal);
  display: flex;
  align-items: center;
  justify-content: center;
  font-family: var(--font-display);
  font-size: 1.5rem;
  font-weight: 700;
  color: var(--white);
}

.seele-card__body h3 {
  font-size: 1.05rem;
  font-weight: 600;
  margin-bottom: 0.2rem;
}

.seele-card__body p {
  font-size: 0.85rem;
  color: rgba(255,255,255,0.5);
}

@media (max-width: 768px) {
  .seele__layout {
    grid-template-columns: 1fr;
    gap: 2.5rem;
  }

  .seele__left {
    position: static;
  }
}
</style>
