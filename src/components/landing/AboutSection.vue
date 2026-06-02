<template>
  <section id="sobre" class="about-section landing-section">
    <div class="landing-container">
      <div class="about-section__grid">
        <q-card flat class="about-section__card about-section__content-card">
          <q-card-section>
            <h2 class="about-section__title">
              Quem é a
              <span class="text-movve-green">movve</span>
            </h2>
            <p class="about-section__text">
              A MOVVE é uma empresa especializada em ginástica laboral e qualidade de vida
              corporativa, com foco em saúde física, mental e bem-estar no ambiente de trabalho.
            </p>

            <div class="about-section__items">
              <div v-for="item in cards" :key="item.text" class="about-section__item">
                <q-icon :name="item.icon" :class="item.iconClass" size="64px" />
                <p class="about-section__card-text">{{ item.text }}</p>
              </div>
            </div>
          </q-card-section>
        </q-card>

        <div class="about-section__image-placeholder" aria-label="Ilustração de ginástica laboral">
          <div
            class="about-section__splash-frame"
            role="img"
            aria-label="Movve Woman"
            :style="{
              '--splash-image': `url(${splashMask})`,
              '--illustration-image': `url(${movveWoman1})`,
            }"
          ></div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import splashMask from 'assets/backgrounds/mask.png'
import movveWoman1 from 'assets/illustrations/woman-home-office-1.svg'

const cards = [
  {
    icon: 'mdi-heart-pulse',
    iconClass: 'text-movve-green',
    text: 'Mais saúde e disposição',
  },
  {
    icon: 'mdi-target',
    iconClass: 'text-movve-blue',
    text: 'Mais produtividade e foco',
  },
  {
    icon: 'mdi-account-group',
    iconClass: 'text-movve-green',
    text: 'Mais integração e motivação',
  },
  {
    icon: 'mdi-emoticon-happy-outline',
    iconClass: 'text-movve-blue',
    text: 'Mais qualidade de vida',
  },
]
</script>

<style lang="scss" scoped>
.about-section {
  padding: 104px 0;
  background: var(--movve-background);
}

.about-section__grid {
  min-height: 360px;
  display: grid;
  grid-template-columns: minmax(0, 1.12fr) minmax(360px, 0.88fr);
  align-items: center;
  gap: 48px;
}

.about-section__title {
  max-width: 520px;
  margin: 0;
  color: var(--movve-blue);
  font-size: clamp(2rem, 4vw, 3.3rem);
  font-weight: 850;
  line-height: 1.08;
}

.about-section__text {
  max-width: 760px;
  margin: 28px 0 0;
  color: #4b5563;
  font-size: 1.05rem;
  line-height: 1.75;
}

.about-section__card {
  background: transparent;
  border-radius: 8px;
  color: #4b5563;
  font-size: 1.05rem;
  line-height: 1.75;
}

.about-section__content-card {
  min-height: 420px;
  display: flex;
  align-items: center;
}

.about-section__items {
  display: grid;
  grid-template-columns: repeat(4, minmax(0, 1fr));
  gap: 22px;
  margin-top: 36px;
}

.about-section__item {
  text-align: center;
}

.about-section__card-text {
  margin: 18px 0 0;
  color: #233c55;
  font-size: 1rem;
  font-weight: 700;
  line-height: 1.4;
}

.about-section__image-placeholder {
  position: relative;
  min-height: 420px;
  display: grid;
  place-items: center;
  align-content: center;
  text-align: center;
}

.about-section__splash-frame {
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
  .about-section {
    padding: 72px 0;
  }

  .about-section__grid {
    min-height: 420px;
    grid-template-columns: 1fr;
    gap: 28px;
  }

  .about-section__items {
    grid-template-columns: repeat(2, minmax(0, 1fr));
  }

  .about-section__content-card,
  .about-section__image-placeholder {
    min-height: auto;
  }

  .about-section__image-placeholder {
    display: none;
  }
}
</style>
