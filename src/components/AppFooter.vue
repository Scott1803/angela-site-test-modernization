<script setup lang="ts">
const year = new Date().getFullYear()
</script>

<template>
  <footer class="footer">
    <div class="footer__inner container">
      <div class="footer__grid">
        <div class="footer__brand">
          <h3 class="footer__name">Angela Einicke</h3>
          <p class="footer__subtitle">Diplom-Psychologin</p>
          <p class="footer__tagline">
            Systemisch. Einfühlsam. Lösungsorientiert.
          </p>
        </div>

        <div class="footer__col">
          <h4>Leistungen</h4>
          <ul>
            <li><router-link to="/leistungen#beratung">Psychologische Beratung</router-link></li>
            <li><router-link to="/leistungen#sprechstunde">Sprechstunde Psyche</router-link></li>
            <li><router-link to="/leistungen#schulungen">Schulungen</router-link></li>
            <li><router-link to="/leistungen#seminare">Seminare</router-link></li>
          </ul>
        </div>

        <div class="footer__col">
          <h4>Kontakt</h4>
          <ul>
            <li>
              <a href="tel:06151317027">06151 317027</a>
            </li>
            <li>
              <a href="mailto:info@psychologin-angelaeinicke.de">info@psychologin-angelaeinicke.de</a>
            </li>
            <li>Erbacher Str. 109</li>
            <li>64287 Darmstadt</li>
          </ul>
        </div>
      </div>

      <div class="footer__bottom">
        <p>&copy; {{ year }} Angela Einicke. Alle Rechte vorbehalten.</p>
      </div>
    </div>
  </footer>
</template>

<style scoped>
.footer {
  background: var(--gray-900);
  color: rgba(255, 255, 255, 0.6);
  padding: 4rem 0 0;
  margin-top: auto;
}

.footer__grid {
  display: grid;
  grid-template-columns: 1.5fr 1fr 1fr;
  gap: 3rem;
}

.footer__name {
  font-family: var(--font-display);
  font-size: 1.5rem;
  color: var(--white);
  font-weight: 600;
}

.footer__subtitle {
  font-size: 0.75rem;
  text-transform: uppercase;
  letter-spacing: 0.15em;
  color: var(--teal);
  margin-top: 0.25rem;
}

.footer__tagline {
  margin-top: 1rem;
  font-size: 0.9rem;
  line-height: 1.6;
}

.footer__col h4 {
  color: var(--white);
  font-size: 0.85rem;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.1em;
  margin-bottom: 1rem;
}

.footer__col ul {
  list-style: none;
  display: flex;
  flex-direction: column;
  gap: 0.6rem;
}

.footer__col a {
  font-size: 0.875rem;
  transition: color 0.3s ease;
}

.footer__col a:hover {
  color: var(--teal-light);
}

.footer__col li {
  font-size: 0.875rem;
}

.footer__bottom {
  border-top: 1px solid rgba(255, 255, 255, 0.08);
  margin-top: 3rem;
  padding: 1.5rem 0;
  text-align: center;
  font-size: 0.8rem;
}

@media (max-width: 768px) {
  .footer__grid {
    grid-template-columns: 1fr;
    gap: 2rem;
  }
}
</style>
