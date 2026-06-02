<template>
  <footer id="contatos" class="app-footer landing-section">
    <div class="landing-container">
      <h2>
        Vamos
        <span class="text-movve-green">movver juntos?</span>
      </h2>

      <div class="app-footer__inner">
        <div class="app-footer__content">
          <p class="app-footer__text">
            Cuidar de quem move sua empresa é o que nos move todos os dias.
          </p>
          <p class="app-footer__highlight">
            Conte com a movve para levar saúde, energia e bem estar para o seu time!
          </p>
        </div>

        <div class="app-footer__contacts" aria-label="Contatos Movve">
          <a
            v-for="contact in contacts"
            :key="contact.text"
            class="app-footer__contact"
            :href="contact.href"
            target="_blank"
            rel="noopener noreferrer"
          >
            <q-icon :name="contact.icon" :style="{ color: contact.color }" size="30px" />
            <span>{{ contact.text }}</span>
          </a>
        </div>
      </div>
    </div>
  </footer>
</template>

<script setup>
const contacts = [
  {
    icon: 'mdi-instagram',
    color: '#e4405f',
    text: '@movve.corporativo',
    href: 'https://www.instagram.com/movve.corporativo',
  },
  {
    icon: 'mdi-email-outline',
    color: 'var(--movve-blue)',
    text: 'movve.ginasticalaboral@gmail.com',
    href: 'mailto:movve.ginasticalaboral@gmail.com',
  },
  {
    icon: 'mdi-whatsapp',
    color: '#25d366',
    text: '48 992229310',
    href: 'https://wa.me/5548992229310',
  },
]
</script>

<style lang="scss" scoped>
.app-footer {
  padding: 88px 0;
  background: var(--movve-blue);
  color: #ffffff;
}

.app-footer__inner {
  margin-top: 34px;
  display: grid;
  grid-template-columns: minmax(0, 0.6fr) minmax(280px, 0.4fr);
  gap: 48px;
  align-items: stretch;
}

.app-footer__content {
  display: flex;
  flex-direction: column;
  justify-content: center;
}

h2 {
  margin: 0;
  font-size: clamp(2rem, 4vw, 3.1rem);
  font-weight: 850;
  line-height: 1.08;
}

.app-footer__text {
  max-width: 520px;
  margin: 0;
  color: #ffffff;
  font-size: clamp(1.2rem, 2vw, 1.45rem);
  font-weight: 650;
  line-height: 1.6;
}

.app-footer__highlight {
  max-width: 560px;
  margin: 18px 0 0;
  color: var(--movve-green);
  font-size: clamp(1.2rem, 2vw, 1.45rem);
  font-weight: 800;
  line-height: 1.55;
}

.app-footer__contacts {
  display: grid;
  gap: 18px;
}

.app-footer__contact {
  display: flex;
  align-items: center;
  gap: 16px;
  min-height: 62px;
  padding: 14px 16px;
  border: 1px solid rgba(255, 255, 255, 0.14);
  border-radius: 8px;
  background: rgba(255, 255, 255, 0.09);
  color: #ffffff;
  font-size: 1.05rem;
  font-weight: 700;
  line-height: 1.35;
  text-decoration: none;
  transition:
    transform 180ms ease,
    background 180ms ease;
}

.app-footer__contact:hover {
  transform: translateY(-2px);
  background: rgba(255, 255, 255, 0.13);
}

@media (max-width: 760px) {
  .app-footer__inner {
    grid-template-columns: 1fr;
    gap: 28px;
  }
}
</style>
