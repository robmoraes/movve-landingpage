<template>
  <section id="beneficios" class="benefits-section landing-section">
    <div class="landing-container">
      <div class="benefits-section__grid">
        <div class="benefits-section__image-placeholder" aria-label="Ilustração futura">
          <div
            class="benefits-section__splash-frame"
            role="img"
            aria-label="Mulher sentada fazendo exercício com elástico"
            :style="{
              '--splash-image': `url(${splashMask})`,
              '--illustration-image': `url(${seatedWoman})`,
            }"
          ></div>
        </div>

        <q-card flat class="benefits-section__card benefits-section__content-card">
          <q-card-section>
            <h2 class="benefits-section__title">
              Benefícios para sua
              <span class="text-movve-green">empresa</span>
            </h2>

            <div class="benefits-section__items">
              <div v-for="item in items" :key="item.text" class="benefits-section__item">
                <q-icon :name="item.icon" :class="item.iconClass" size="64px" />
                <p class="benefits-section__item-text">{{ item.text }}</p>
              </div>
            </div>
          </q-card-section>
        </q-card>
      </div>
    </div>
  </section>
</template>

<script setup>
import splashMask from 'assets/backgrounds/mask.png'
import seatedWoman from 'assets/illustrations/seated-woman-with-resistance-band-2.svg'

const items = [
  {
    icon: 'mdi-account-outline',
    iconClass: 'text-movve-green',
    text: 'Redução do estresse e da ansiedade',
  },
  {
    icon: 'mdi-shield-check-outline',
    iconClass: 'text-movve-blue',
    text: 'Prevenção de dores e lesões',
  },
  {
    icon: 'mdi-lightning-bolt-outline',
    iconClass: 'text-movve-green',
    text: 'Mais foco, energia e produtividade',
  },
  {
    icon: 'mdi-emoticon-happy-outline',
    iconClass: 'text-movve-blue',
    text: 'Melhora do clima organizacional',
  },
  {
    icon: 'mdi-account-group-outline',
    iconClass: 'text-movve-green',
    text: 'Maior integração entre equipes',
  },
  {
    icon: 'mdi-heart-pulse',
    iconClass: 'text-movve-blue',
    text: 'Promoção da saúde e bem-estar',
  },
]
</script>

<style lang="scss" scoped>
.benefits-section {
  padding: 104px 0;
  background: var(--movve-background);
}

.benefits-section__grid {
  min-height: 360px;
  display: grid;
  grid-template-columns: minmax(280px, 0.65fr) minmax(0, 1.35fr);
  align-items: center;
  gap: 48px;
}

.benefits-section__title {
  max-width: 620px;
  margin: 0;
  color: var(--movve-blue);
  font-size: clamp(2rem, 4vw, 3.3rem);
  font-weight: 850;
  line-height: 1.08;
}

.benefits-section__card {
  background: transparent;
  border-radius: 8px;
  color: #4b5563;
  font-size: 1.05rem;
  line-height: 1.75;
}

.benefits-section__content-card {
  min-height: 420px;
  display: flex;
  align-items: center;
}

.benefits-section__items {
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  gap: 28px 24px;
  margin-top: 36px;
}

.benefits-section__item {
  text-align: center;
}

.benefits-section__item-text {
  margin: 16px 0 0;
  color: #233c55;
  font-size: 1rem;
  font-weight: 700;
  line-height: 1.4;
}

.benefits-section__image-placeholder {
  min-height: 420px;
  display: grid;
  place-items: center;
  align-content: center;
  text-align: center;
}

.benefits-section__splash-frame {
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
  .benefits-section {
    padding: 72px 0;
  }

  .benefits-section__grid {
    min-height: 420px;
    grid-template-columns: 1fr;
    gap: 28px;
  }

  .benefits-section__content-card,
  .benefits-section__image-placeholder {
    min-height: auto;
  }

  .benefits-section__items {
    grid-template-columns: 1fr;
  }

  .benefits-section__image-placeholder {
    display: none;
  }
}
</style>
