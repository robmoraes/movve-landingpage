<template>
  <section id="missao" class="mission-section landing-section">
    <div class="landing-container">
      <div class="mission-section__grid">
        <q-card flat class="mission-section__card mission-section__content-card">
          <q-card-section>
            <h2 class="mission-section__title">
              Nossa
              <span class="text-movve-green">missão</span>
            </h2>

            <blockquote class="mission-section__quote">
              Promover saúde, movimento e bem-estar por meio de pausas inteligentes, transformando o
              ambiente de trabalho em um lugar mais leve, saudável e humano.
            </blockquote>

            <img :src="movveLogo" alt="Movve" class="mission-section__logo" />
          </q-card-section>
        </q-card>

        <div class="mission-section__image-placeholder" aria-label="Ilustração futura">
          <div
            class="mission-section__splash-frame"
            role="img"
            aria-label="Mulher trabalhando em home office"
            :style="{
              '--splash-image': `url(${splashMask})`,
              '--illustration-image': `url(${womanHomeOffice})`,
            }"
          ></div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import splashMask from 'assets/backgrounds/mask.png'
import movveLogo from 'assets/branding/logo/movve-logo.svg'
import womanHomeOffice from 'assets/illustrations/woman-home-office-2.svg'
</script>

<style lang="scss" scoped>
.mission-section {
  padding: 104px 0;
  background: var(--movve-background);
}

.mission-section__grid {
  min-height: 360px;
  display: grid;
  grid-template-columns: minmax(0, 1.35fr) minmax(280px, 0.65fr);
  align-items: center;
  gap: 48px;
}

.mission-section__title {
  max-width: 620px;
  margin: 0;
  color: var(--movve-blue);
  font-size: clamp(2rem, 4vw, 3.3rem);
  font-weight: 850;
  line-height: 1.08;
}

.mission-section__card {
  background: transparent;
  border-radius: 8px;
  color: #4b5563;
}

.mission-section__content-card {
  min-height: 420px;
  display: flex;
  align-items: center;
}

.mission-section__quote {
  position: relative;
  margin: 34px 0 0;
  padding: 28px 30px;
  border-left: 5px solid var(--movve-green);
  border-radius: 8px;
  background: var(--movve-light-blue);
  color: #233c55;
  font-size: clamp(1.25rem, 2vw, 1.7rem);
  font-weight: 750;
  line-height: 1.48;
}

.mission-section__quote::before,
.mission-section__quote::after {
  color: var(--movve-green);
  font-size: 2.3rem;
  font-weight: 850;
  line-height: 1;
}

.mission-section__quote::before {
  content: '"';
  margin-right: 4px;
}

.mission-section__quote::after {
  content: '"';
  margin-left: 4px;
}

.mission-section__logo {
  height: clamp(180px, 24vw, 320px);
  width: auto;
  max-width: min(100%, 720px);
  margin: 34px auto 0;
  display: block;
}

.mission-section__image-placeholder {
  min-height: 420px;
  display: grid;
  place-items: center;
  align-content: center;
  text-align: center;
}

.mission-section__splash-frame {
  position: relative;
  width: min(118%, 520px);
  aspect-ratio: 1 / 1.36;
  overflow: hidden;
  background: var(--illustration-image) center / 106% no-repeat;
  filter: drop-shadow(0 28px 48px rgba(4, 50, 113, 0.16));
  mask-image: var(--splash-image);
  mask-mode: luminance;
  mask-repeat: no-repeat;
  mask-size: 100% 100%;
  mask-position: center;
  -webkit-mask-image: var(--splash-image);
  -webkit-mask-repeat: no-repeat;
  -webkit-mask-size: 100% 100%;
  -webkit-mask-position: center;
}

@media (max-width: 760px) {
  .mission-section {
    padding: 72px 0;
  }

  .mission-section__grid {
    min-height: 420px;
    grid-template-columns: 1fr;
    gap: 28px;
  }

  .mission-section__content-card,
  .mission-section__image-placeholder {
    min-height: auto;
  }

  .mission-section__image-placeholder {
    display: none;
  }
}
</style>
