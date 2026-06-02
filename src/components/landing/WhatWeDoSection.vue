<template>
  <section id="o-que-fazemos" class="what-section landing-section">
    <div class="landing-container">
      <div class="what-section__grid">
        <div class="what-section__image-placeholder" aria-label="Ilustração futura">
          <div
            class="what-section__splash-frame"
            role="img"
            aria-label="Mulher fazendo alongamento corporativo"
            :style="{
              '--splash-image': `url(${splashMask})`,
              '--illustration-image': `url(${standingWoman})`,
            }"
          ></div>
        </div>

        <q-card flat class="what-section__card what-section__content-card">
          <q-card-section>
            <h2 class="what-section__title">
              O que
              <span class="text-movve-green">fazemos</span>
            </h2>

            <p class="what-section__text">
              Oferecemos programas de ginástica laboral e bem-estar corporativo que promovem saúde,
              previnem doenças e melhoram o clima organizacional.
            </p>

            <q-list class="what-section__list">
              <q-item v-for="item in items" :key="item" dense class="what-section__list-item">
                <q-item-section avatar>
                  <q-icon name="mdi-check-circle" class="text-movve-green" size="24px" />
                </q-item-section>
                <q-item-section>{{ item }}</q-item-section>
              </q-item>
            </q-list>
          </q-card-section>
        </q-card>
      </div>
    </div>
  </section>
</template>

<script setup>
import splashMask from 'assets/backgrounds/mask.png'
import standingWoman from 'assets/illustrations/standing-woman-1.svg'

const items = [
  'Ginástica Laboral',
  'Laboral Neuroativa',
  'Alongamento Corporativo',
  'Relaxamento e Respiração',
  'Pausas Inteligentes',
  'Ativação Corporal Rápida',
]
</script>

<style lang="scss" scoped>
.what-section {
  padding: 104px 0;
  background: var(--movve-light-blue);
}

.what-section__grid {
  min-height: 360px;
  display: grid;
  grid-template-columns: minmax(280px, 0.65fr) minmax(0, 1.35fr);
  align-items: center;
  gap: 48px;
}

.what-section__title {
  max-width: 520px;
  margin: 0;
  color: var(--movve-blue);
  font-size: clamp(2rem, 4vw, 3.3rem);
  font-weight: 850;
  line-height: 1.08;
}

.what-section__text {
  max-width: 760px;
  margin: 28px 0 0;
  color: #4b5563;
  font-size: 1.05rem;
  line-height: 1.75;
}

.what-section__card {
  background: transparent;
  border-radius: 8px;
  color: #4b5563;
  font-size: 1.05rem;
  line-height: 1.75;
}

.what-section__content-card {
  min-height: 420px;
  display: flex;
  align-items: center;
}

.what-section__list {
  display: grid;
  grid-template-columns: 1fr;
  gap: 6px;
  margin-top: 28px;
}

.what-section__list-item {
  padding-left: 0;
  color: #233c55;
  font-weight: 700;
}

.what-section__image-placeholder {
  min-height: 420px;
  display: grid;
  place-items: center;
  align-content: center;
  text-align: center;
}

.what-section__splash-frame {
  position: relative;
  width: min(118%, 520px);
  aspect-ratio: 1 / 1.36;
  overflow: hidden;
  background: var(--illustration-image) center / 96% no-repeat;
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
  .what-section {
    padding: 72px 0;
  }

  .what-section__grid {
    min-height: 420px;
    grid-template-columns: 1fr;
    gap: 28px;
  }

  .what-section__content-card,
  .what-section__image-placeholder {
    min-height: auto;
  }

  .what-section__image-placeholder {
    display: none;
  }
}
</style>
