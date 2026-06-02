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
          <q-icon name="mdi-image-outline" size="54px" class="text-movve-blue" />
          <p>Ilustração do funcionamento</p>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
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
  gap: 16px;
  border: 1px dashed rgba(4, 50, 113, 0.24);
  border-radius: 8px;
  background: rgba(255, 255, 255, 0.52);
  color: #4b5563;
  text-align: center;
}

.how-section__image-placeholder p {
  max-width: 180px;
  margin: 0;
  font-weight: 700;
  line-height: 1.35;
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
