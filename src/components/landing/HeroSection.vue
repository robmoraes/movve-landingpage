<template>
  <section id="hero" class="hero-section landing-section">
    <div class="hero-section__texture" aria-hidden="true"></div>
    <div class="hero-section__shape hero-section__shape--blue" aria-hidden="true"></div>
    <div class="hero-section__shape hero-section__shape--green" aria-hidden="true"></div>

    <div class="landing-container hero-section__layout">
      <div class="hero-section__content">
        <div class="hero-section__headline-block">
          <p class="hero-section__eyebrow">Saude corporativa em movimento</p>
          <div class="hero-section__copy-set">
            <Transition name="hero-headline" mode="out-in">
              <h1 :key="activeHeroCopy.destaque">
                <span
                  v-for="(part, index) in activeHeroCopy.destaqueParts"
                  :key="`destaque-${index}`"
                  :class="{ 'hero-section__highlight': part.highlight }"
                >
                  {{ part.text }}
                </span>
              </h1>
            </Transition>

            <Transition name="hero-subheadline" mode="out-in">
              <p :key="activeHeroCopy.apoio" class="hero-section__subheadline">
                <span
                  v-for="(part, index) in activeHeroCopy.apoioParts"
                  :key="`apoio-${index}`"
                  :class="{ 'hero-section__highlight': part.highlight }"
                >
                  {{ part.text }}
                </span>
              </p>
            </Transition>
          </div>
        </div>

        <div class="hero-section__trust" aria-label="Indicadores de credibilidade">
          <span v-for="item in trustItems" :key="item">{{ item }}</span>
        </div>

        <div class="hero-section__actions">
          <q-btn
            unelevated
            no-caps
            class="hero-section__cta hero-section__cta--primary"
            icon="mdi-whatsapp"
            label="Falar com a Movve"
            href="https://wa.me/5548992229310"
            target="_blank"
            rel="noopener noreferrer"
          />
          <q-btn
            outline
            no-caps
            class="hero-section__cta hero-section__cta--secondary"
            label="Conhecer a proposta"
            @click="scrollToSection('sobre')"
          />
        </div>
      </div>

      <div class="hero-section__visual" aria-hidden="true">
        <div class="hero-section__motion-line hero-section__motion-line--one"></div>
        <div class="hero-section__motion-line hero-section__motion-line--two"></div>
        <div class="hero-section__motion-line hero-section__motion-line--three"></div>

        <div class="hero-section__glass hero-section__glass--top"></div>
        <div class="hero-section__glass hero-section__glass--bottom"></div>

        <div class="hero-section__mark">
          <div class="hero-section__mark-glow"></div>
          <img :src="movveIcon" alt="" class="hero-section__icon" />
        </div>

        <div class="hero-section__brand" aria-label="Movve">
          <img :src="movveWordmark" alt="Movve" class="hero-section__wordmark" />
          <img :src="movveTagline" alt="Tagline Movve" class="hero-section__tagline" />
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { computed, onBeforeUnmount, onMounted, ref } from 'vue'
import movveIcon from 'assets/branding/logo/movve-icon.svg'
import movveTagline from 'assets/branding/logo/movve-tagline.svg'
import movveWordmark from 'assets/branding/logo/movve-wordmark.svg'

const heroCopyItems = [
  {
    destaque:
      'Ginástica laboral que aumenta o <g>bem-estar</g> e a <g>produtividade</g> da sua equipe.',
    apoio:
      'Aulas rápidas de 8 a 15 minutos, presenciais ou online, para <g>reduzir o estresse</g>, <g>prevenir dores</g> e promover <g>saúde</g> no ambiente de trabalho.',
  },
  {
    destaque: '<g>Saúde</g> corporativa que gera <g>resultados</g> reais.',
    apoio:
      'Programas de ginástica laboral desenvolvidos para melhorar o <g>clima organizacional</g>, <g>reduzir afastamentos</g> e aumentar o <g>engajamento</g> das equipes.',
  },
  {
    destaque:
      'Transforme o ambiente de trabalho em um espaço mais <g>saudável</g>, <g>produtivo</g> e <g>humano</g>.',
    apoio:
      'A MOVVE leva <g>pausas inteligentes</g>, <g>movimento</g> e <g>bem-estar</g> para empresas que valorizam pessoas.',
  },
  {
    destaque: 'Menos estresse. Mais <g>energia</g>. Mais <g>produtividade</g>.',
    apoio:
      'Programas de ginástica laboral que cuidam da <g>saúde física e mental</g> dos colaboradores.',
  },
  {
    destaque: 'Colaboradores <g>saudáveis</g> constroem empresas mais <g>fortes</g>.',
    apoio:
      'Promovemos <g>saúde</g>, movimento e <g>bem-estar</g> por meio de pausas inteligentes no ambiente corporativo.',
  },
]

const trustItems = ['Saude corporativa', 'Bem-estar', 'Produtividade', 'Integracao']
const activeHeroCopyIndex = ref(0)
const activeHeroCopy = computed(() => {
  const copy = heroCopyItems[activeHeroCopyIndex.value]

  return {
    ...copy,
    destaqueParts: parseGreenTags(copy.destaque),
    apoioParts: parseGreenTags(copy.apoio),
  }
})

let heroCopyTimer

onMounted(() => {
  heroCopyTimer = window.setInterval(() => {
    activeHeroCopyIndex.value = (activeHeroCopyIndex.value + 1) % heroCopyItems.length
  }, 10000)
})

onBeforeUnmount(() => {
  window.clearInterval(heroCopyTimer)
})

function scrollToSection(id) {
  document.getElementById(id)?.scrollIntoView({ behavior: 'smooth', block: 'start' })
}

function parseGreenTags(text) {
  return text
    .split(/(<g>.*?<\/g>)/)
    .filter(Boolean)
    .map((part) => {
      const match = part.match(/^<g>(.*?)<\/g>$/)

      return {
        text: match?.[1] ?? part,
        highlight: Boolean(match),
      }
    })
}
</script>

<style lang="scss" scoped>
.hero-section {
  position: relative;
  min-height: 90vh;
  padding: 148px 0 88px;
  display: flex;
  align-items: center;
  background:
    radial-gradient(
      circle at 0% 50%,
      rgba(4, 50, 113, 0.27) 0%,
      rgba(4, 50, 113, 0.12) 34%,
      rgba(4, 50, 113, 0) 58%
    ),
    radial-gradient(
      circle at 100% 50%,
      rgba(4, 50, 113, 0.3) 0%,
      rgba(4, 50, 113, 0.14) 36%,
      rgba(4, 50, 113, 0) 62%
    ),
    radial-gradient(
      circle at 70% 24%,
      rgba(4, 50, 113, 0.12) 0%,
      rgba(4, 50, 113, 0.05) 32%,
      rgba(4, 50, 113, 0) 54%
    ),
    linear-gradient(90deg, #e0eaf4 0%, #f6faff 44%, #eef4fb 66%, #dfe9f3 100%);
  overflow: hidden;
}

.hero-section::after {
  content: '';
  position: absolute;
  inset: auto 0 0;
  height: 120px;
  background: linear-gradient(180deg, rgba(255, 255, 255, 0), #ffffff);
  pointer-events: none;
}

.hero-section__texture {
  position: absolute;
  inset: 0;
  background-image:
    linear-gradient(rgba(4, 50, 113, 0.045) 1px, transparent 1px),
    linear-gradient(90deg, rgba(4, 50, 113, 0.035) 1px, transparent 1px);
  background-size: 44px 44px;
  mask-image: linear-gradient(90deg, transparent, #000 18%, #000 78%, transparent);
  opacity: 0.42;
  pointer-events: none;
}

.hero-section__shape {
  position: absolute;
  border-radius: 999px;
  filter: blur(54px);
  opacity: 0.5;
  pointer-events: none;
}

.hero-section__shape--blue {
  top: 9%;
  right: 6%;
  width: 380px;
  height: 260px;
  background: rgba(4, 50, 113, 0.12);
  transform: rotate(-18deg);
}

.hero-section__shape--green {
  right: 28%;
  bottom: 7%;
  width: 420px;
  height: 210px;
  background: rgba(4, 50, 113, 0.1);
  transform: rotate(16deg);
}

.hero-section__layout {
  position: relative;
  z-index: 1;
  display: grid;
  grid-template-columns: minmax(0, 1fr) minmax(340px, 0.82fr);
  align-items: center;
  gap: clamp(48px, 7vw, 92px);
}

.hero-section__content {
  max-width: 700px;
  animation: hero-content-in 680ms ease-out both;
}

.hero-section__brand {
  position: relative;
  z-index: 4;
  width: min(100%, 360px);
  display: grid;
  gap: 12px;
  margin-top: -18px;
  justify-items: center;
}

.hero-section__wordmark,
.hero-section__tagline {
  display: block;
  width: 100%;
  height: auto;
}

.hero-section__tagline {
  width: min(100%, 360px);
}

.hero-section__headline-block {
  margin-top: 0;
}

.hero-section__eyebrow {
  margin: 0 0 18px;
  color: var(--movve-green);
  font-size: 0.78rem;
  font-weight: 800;
  letter-spacing: 0.08em;
  text-transform: uppercase;
}

h1 {
  max-width: 620px;
  margin: 0;
  color: var(--movve-blue);
  font-size: clamp(2rem, 3.05vw, 3.25rem);
  font-weight: 850;
  letter-spacing: 0;
  line-height: 1.04;
}

.hero-section__highlight {
  color: var(--movve-green);
}

.hero-section__subheadline {
  max-width: 610px;
  margin: 28px 0 0;
  color: #324a63;
  font-size: clamp(1.05rem, 1.35vw, 1.24rem);
  line-height: 1.72;
}

.hero-headline-enter-active,
.hero-headline-leave-active,
.hero-subheadline-enter-active,
.hero-subheadline-leave-active {
  transition:
    opacity 440ms cubic-bezier(0.22, 1, 0.36, 1),
    transform 440ms cubic-bezier(0.22, 1, 0.36, 1);
}

.hero-subheadline-enter-active {
  transition-delay: 140ms;
}

.hero-headline-enter-from,
.hero-subheadline-enter-from {
  opacity: 0;
  transform: translateY(12px);
}

.hero-headline-leave-to,
.hero-subheadline-leave-to {
  opacity: 0;
  transform: translateY(-10px);
}

.hero-section__trust {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
  margin-top: 30px;
}

.hero-section__trust span {
  display: inline-flex;
  align-items: center;
  min-height: 34px;
  padding: 6px 12px;
  border: 1px solid rgba(4, 50, 113, 0.1);
  border-radius: 999px;
  background: rgba(255, 255, 255, 0.56);
  color: #233c55;
  font-size: 0.9rem;
  font-weight: 650;
  backdrop-filter: blur(14px);
}

.hero-section__trust span::before {
  content: '';
  width: 7px;
  height: 7px;
  margin-right: 8px;
  border-radius: 50%;
  background: var(--movve-green);
  box-shadow: 0 0 0 4px rgba(118, 181, 60, 0.12);
}

.hero-section__actions {
  display: flex;
  flex-wrap: wrap;
  gap: 14px;
  margin-top: 38px;
}

.hero-section__cta {
  min-height: 50px;
  padding: 0 22px;
  border-radius: 8px;
  font-weight: 750;
  transition:
    transform 180ms ease,
    box-shadow 180ms ease,
    background-color 180ms ease;
}

.hero-section__cta:hover {
  transform: translateY(-2px);
}

.hero-section__cta--primary {
  background: #25d366;
  color: #ffffff;
  box-shadow: 0 16px 38px rgba(37, 211, 102, 0.28);
}

.hero-section__cta--primary:hover {
  box-shadow: 0 20px 48px rgba(37, 211, 102, 0.34);
}

.hero-section__cta--secondary {
  color: var(--movve-blue);
}

.hero-section__visual {
  position: relative;
  min-height: 520px;
  display: grid;
  place-items: center;
  align-content: center;
  animation: hero-visual-in 760ms ease-out 100ms both;
}

.hero-section__mark {
  position: relative;
  z-index: 3;
  width: min(90%, 430px);
  aspect-ratio: 1;
  display: grid;
  place-items: center;
  animation: hero-float 7s ease-in-out infinite;
}

.hero-section__mark-glow {
  position: absolute;
  inset: 18%;
  border-radius: 44% 56% 58% 42%;
  background: rgba(118, 181, 60, 0.18);
  filter: blur(34px);
}

.hero-section__icon {
  position: relative;
  z-index: 1;
  width: 82%;
  height: auto;
  filter: drop-shadow(0 32px 46px rgba(4, 50, 113, 0.2));
}

.hero-section__glass {
  position: absolute;
  z-index: 1;
  border: 1px solid rgba(255, 255, 255, 0.72);
  border-radius: 8px;
  background: rgba(255, 255, 255, 0.28);
  box-shadow: 0 24px 56px rgba(4, 50, 113, 0.08);
  backdrop-filter: blur(18px);
}

.hero-section__glass--top {
  top: 6%;
  right: 4%;
  width: 118px;
  height: 82px;
}

.hero-section__glass--bottom {
  left: 4%;
  bottom: 8%;
  width: 150px;
  height: 96px;
}

.hero-section__motion-line {
  position: absolute;
  z-index: 0;
  height: 1px;
  background: linear-gradient(
    90deg,
    rgba(4, 50, 113, 0),
    rgba(4, 50, 113, 0.2),
    rgba(118, 181, 60, 0)
  );
  transform-origin: center;
}

.hero-section__motion-line--one {
  top: 22%;
  width: min(92vw, 620px);
  transform: rotate(-18deg);
}

.hero-section__motion-line--two {
  top: 52%;
  width: min(80vw, 520px);
  transform: rotate(12deg);
}

.hero-section__motion-line--three {
  bottom: 18%;
  width: min(70vw, 470px);
  transform: rotate(-8deg);
}

@keyframes hero-content-in {
  from {
    opacity: 0;
    transform: translateY(16px);
  }

  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes hero-visual-in {
  from {
    opacity: 0;
    transform: translateX(18px) scale(0.98);
  }

  to {
    opacity: 1;
    transform: translateX(0) scale(1);
  }
}

@keyframes hero-float {
  0%,
  100% {
    transform: translate3d(0, 0, 0);
  }

  50% {
    transform: translate3d(0, -14px, 0);
  }
}

@media (max-width: 1023px) {
  .hero-section {
    min-height: 100vh;
    padding: 112px 0 64px;
    align-items: center;
  }

  .hero-section__layout {
    grid-template-columns: 1fr;
    justify-items: center;
    gap: 30px;
    text-align: center;
  }

  .hero-section__content {
    order: 2;
    width: 100%;
    max-width: 430px;
    display: grid;
    justify-items: center;
  }

  .hero-section__headline-block,
  .hero-section__trust {
    display: none;
  }

  .hero-section__actions {
    justify-content: center;
    margin-top: 0;
  }

  .hero-section__visual {
    order: 1;
    width: 100%;
    min-height: auto;
    place-items: center;
    align-content: center;
  }

  .hero-section__mark {
    width: min(58vw, 280px);
  }

  .hero-section__brand {
    width: min(74vw, 320px);
    margin-top: -10px;
  }

  .hero-section__glass,
  .hero-section__motion-line {
    display: none;
  }
}

@media (max-width: 620px) {
  .hero-section {
    padding: 104px 0 52px;
  }

  .hero-section__brand {
    width: min(82vw, 300px);
    gap: 10px;
    margin-top: -12px;
  }

  .hero-section__headline-block {
    margin-top: 38px;
  }

  h1 {
    font-size: clamp(1.82rem, 8vw, 2.4rem);
  }

  .hero-section__trust {
    gap: 8px;
  }

  .hero-section__actions {
    align-items: stretch;
    flex-direction: column;
    width: min(100%, 320px);
  }

  .hero-section__visual {
    min-height: auto;
  }

  .hero-section__mark {
    width: min(66vw, 250px);
  }

  .hero-section__glass {
    display: none;
  }
}
</style>
