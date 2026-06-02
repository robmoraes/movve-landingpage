<template>
  <section id="para-quem-e" class="audience-section landing-section">
    <div class="landing-container">
      <div class="audience-section__grid">
        <div class="audience-section__image-placeholder" aria-label="Ilustração futura">
          <div
            class="audience-section__splash-frame"
            role="img"
            aria-label="Homem em pé fazendo exercício com bolinha de espuma"
            :style="{
              '--splash-image': `url(${splashMask})`,
              '--illustration-image': `url(${standingMan})`,
            }"
          ></div>
        </div>

        <q-card flat class="audience-section__card audience-section__content-card">
          <q-card-section>
            <h2 class="audience-section__title">
              Para quem
              <span class="text-movve-green">é</span>
            </h2>

            <div class="audience-section__items">
              <div v-for="item in items" :key="item.text" class="audience-section__item">
                <q-icon :name="item.icon" :class="item.iconClass" size="64px" />
                <p class="audience-section__item-text">{{ item.text }}</p>
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
import standingMan from 'assets/illustrations/man-standing-with-foam-ball-2.svg'

const items = [
  {
    icon: 'mdi-office-building-outline',
    iconClass: 'text-movve-blue',
    text: 'Empresas de todos os portes',
  },
  {
    icon: 'mdi-account-group-outline',
    iconClass: 'text-movve-green',
    text: 'Todos os setores e áreas',
  },
  {
    icon: 'mdi-heart-outline',
    iconClass: 'text-movve-blue',
    text: 'Equipes que merecem cuidado e atenção',
  },
]
</script>

<style lang="scss" scoped>
.audience-section {
  padding: 104px 0;
  background: var(--movve-light-green);
}

.audience-section__grid {
  min-height: 360px;
  display: grid;
  grid-template-columns: minmax(280px, 0.65fr) minmax(0, 1.35fr);
  align-items: center;
  gap: 48px;
}

.audience-section__title {
  max-width: 620px;
  margin: 0;
  color: var(--movve-blue);
  font-size: clamp(2rem, 4vw, 3.3rem);
  font-weight: 850;
  line-height: 1.08;
}

.audience-section__card {
  background: transparent;
  border-radius: 8px;
  color: #4b5563;
  font-size: 1.05rem;
  line-height: 1.75;
}

.audience-section__content-card {
  min-height: 420px;
  display: flex;
  align-items: center;
}

.audience-section__items {
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  gap: 24px;
  margin-top: 36px;
}

.audience-section__item {
  text-align: center;
}

.audience-section__item-text {
  margin: 16px 0 0;
  color: #233c55;
  font-size: 1rem;
  font-weight: 700;
  line-height: 1.4;
}

.audience-section__image-placeholder {
  min-height: 420px;
  display: grid;
  place-items: center;
  align-content: center;
  text-align: center;
}

.audience-section__splash-frame {
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
  .audience-section {
    padding: 72px 0;
  }

  .audience-section__grid {
    min-height: 420px;
    grid-template-columns: 1fr;
    gap: 28px;
  }

  .audience-section__content-card,
  .audience-section__image-placeholder {
    min-height: auto;
  }

  .audience-section__items {
    grid-template-columns: 1fr;
  }

  .audience-section__image-placeholder {
    display: none;
  }
}
</style>
