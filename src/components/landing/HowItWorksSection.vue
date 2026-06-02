<template>
  <section id="como-funciona" class="how-section landing-section">
    <div class="landing-container">
      <div class="how-section__grid">
        <q-card flat class="how-section__card how-section__content-card">
          <q-card-section>
            <h2 class="how-section__title">
              Como
              <span class="text-movve-green">funciona</span>
            </h2>

            <q-list class="how-section__list">
              <q-item v-for="item in items" :key="item.title" class="how-section__item">
                <q-item-section avatar>
                  <q-icon :name="item.icon" :class="item.iconClass" size="38px" />
                </q-item-section>

                <q-item-section>
                  <q-item-label class="how-section__item-title">{{ item.title }}</q-item-label>
                  <q-item-label caption class="how-section__item-text">
                    {{ item.text }}
                  </q-item-label>
                </q-item-section>
              </q-item>
            </q-list>
          </q-card-section>
        </q-card>

        <div class="how-section__image-placeholder" aria-label="Ilustração futura">
          <div
            class="how-section__splash-frame"
            role="img"
            aria-label="Homem sentado fazendo exercício de ginástica laboral"
            :style="{
              '--splash-image': `url(${splashMask})`,
              '--illustration-image': `url(${seatedMan})`,
            }"
          ></div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import splashMask from 'assets/backgrounds/mask.png'
import seatedMan from 'assets/illustrations/seated-man-1.svg'

const items = [
  {
    icon: 'mdi-clock-outline',
    iconClass: 'text-movve-green',
    title: 'Duração das aulas',
    text: '8 a 15 minutos',
  },
  {
    icon: 'mdi-calendar-month-outline',
    iconClass: 'text-movve-blue',
    title: 'Frequência das aulas',
    text: '2x, 3x ou 5x por semana',
  },
  {
    icon: 'mdi-calendar-check-outline',
    iconClass: 'text-movve-green',
    title: 'Modalidade',
    text: 'Presencial ou Online',
  },
  {
    icon: 'mdi-office-building-marker-outline',
    iconClass: 'text-movve-blue',
    title: 'Onde acontece',
    text: 'No próprio ambiente de trabalho',
  },
]
</script>

<style lang="scss" scoped>
.how-section {
  padding: 104px 0;
  background: var(--movve-light-green);
}

.how-section__grid {
  min-height: 360px;
  display: grid;
  grid-template-columns: minmax(0, 1.35fr) minmax(280px, 0.65fr);
  align-items: center;
  gap: 48px;
}

.how-section__title {
  max-width: 520px;
  margin: 0;
  color: var(--movve-blue);
  font-size: clamp(2rem, 4vw, 3.3rem);
  font-weight: 850;
  line-height: 1.08;
}

.how-section__card {
  background: transparent;
  border-radius: 8px;
  color: #4b5563;
}

.how-section__content-card {
  min-height: 420px;
  display: flex;
  align-items: center;
}

.how-section__list {
  display: grid;
  grid-template-columns: 1fr;
  gap: 12px;
  margin-top: 30px;
}

.how-section__item {
  min-height: 74px;
  padding: 8px;
}

.how-section__item-title {
  color: var(--movve-blue);
  font-size: 1.02rem;
  font-weight: 800;
  line-height: 1.3;
}

.how-section__item-text {
  margin-top: 4px;
  color: #4b5563;
  font-size: 0.98rem;
  font-weight: 600;
  line-height: 1.35;
}

.how-section__image-placeholder {
  min-height: 420px;
  display: grid;
  place-items: center;
  align-content: center;
  text-align: center;
}

.how-section__splash-frame {
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
  .how-section {
    padding: 72px 0;
  }

  .how-section__grid {
    min-height: 420px;
    grid-template-columns: 1fr;
    gap: 28px;
  }

  .how-section__list {
    grid-template-columns: 1fr;
  }

  .how-section__content-card,
  .how-section__image-placeholder {
    min-height: auto;
  }

  .how-section__image-placeholder {
    display: none;
  }
}
</style>
