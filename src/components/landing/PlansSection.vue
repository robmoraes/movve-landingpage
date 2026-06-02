<template>
  <section id="planos" class="plans-section landing-section">
    <div class="landing-container">
      <h2 class="plans-section__title">
        Planos
        <span class="text-movve-green">movve</span>
      </h2>

      <div class="plans-section__cards">
        <q-card v-for="plan in plans" :key="plan.title" flat class="plans-section__card">
          <q-card-section>
            <q-icon :name="plan.icon" class="text-movve-green" size="64px" />
            <h3>{{ plan.title }}</h3>
            <p class="plans-section__subtitle">{{ plan.subtitle }}</p>
            <p class="plans-section__text">{{ plan.text }}</p>
          </q-card-section>
        </q-card>
      </div>

      <div class="plans-section__actions">
        <q-btn
          unelevated
          no-caps
          class="plans-section__cta"
          icon="mdi-whatsapp"
          label="Solicitar Orçamento"
          href="https://wa.me/5548992229310"
          target="_blank"
          rel="noopener noreferrer"
        />
      </div>
    </div>
  </section>
</template>

<script setup>
const plans = [
  {
    icon: 'mdi-calendar-week-outline',
    title: 'Essencial',
    subtitle: '2x por semana',
    text: 'Ideal para começar a transformar o bem-estar de sua equipe.',
  },
  {
    icon: 'mdi-dumbbell',
    title: 'Performance',
    subtitle: '3x por semana',
    text: 'Mais consistência para melhores resultados em saúde e produtividade.',
  },
  {
    icon: 'mdi-laptop',
    title: 'Híbrido',
    subtitle: 'Presencial + Online',
    text: 'Flexibilidade para atender sua equipe onde estiver.',
  },
  {
    icon: 'mdi-account-check-outline',
    title: 'Programas personalizados',
    subtitle: 'Sob medida para sua empresa',
    text: 'Soluções completas e exclusivas de acordo com a necessidade de seu negócio.',
  },
]
</script>

<style lang="scss" scoped>
.plans-section {
  padding: 104px 0;
  background: var(--movve-background);
}

.plans-section__title {
  max-width: 620px;
  margin: 0;
  color: var(--movve-blue);
  font-size: clamp(2rem, 4vw, 3.3rem);
  font-weight: 850;
  line-height: 1.08;
}

.plans-section__cards {
  display: grid;
  grid-template-columns: repeat(4, minmax(0, 1fr));
  gap: 22px;
  margin-top: 42px;
}

.plans-section__card {
  min-height: 300px;
  border: 1px solid rgba(4, 50, 113, 0.1);
  border-radius: 8px;
  color: #4b5563;
  text-align: center;
}

.plans-section__card :deep(.q-card__section) {
  height: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
}

h3 {
  margin: 22px 0 0;
  color: var(--movve-blue);
  font-size: 1.34rem;
  font-weight: 850;
  line-height: 1.18;
}

.plans-section__subtitle {
  margin: 12px 0 0;
  color: var(--movve-green);
  font-size: 1rem;
  font-weight: 850;
  line-height: 1.3;
}

.plans-section__text {
  margin: 16px 0 0;
  color: #4b5563;
  font-size: 1rem;
  font-weight: 600;
  line-height: 1.55;
}

.plans-section__actions {
  margin-top: 38px;
  display: flex;
  justify-content: center;
}

.plans-section__cta {
  min-height: 54px;
  padding: 0 24px;
  border-radius: 999px;
  background: #25d366;
  color: #ffffff;
  font-weight: 800;
  box-shadow: 0 16px 38px rgba(37, 211, 102, 0.28);
  transition:
    transform 180ms ease,
    box-shadow 180ms ease;
}

.plans-section__cta:hover {
  transform: translateY(-2px);
  box-shadow: 0 20px 48px rgba(37, 211, 102, 0.36);
}

@media (max-width: 1023px) {
  .plans-section__cards {
    grid-template-columns: repeat(2, minmax(0, 1fr));
  }
}

@media (max-width: 760px) {
  .plans-section {
    padding: 72px 0;
  }

  .plans-section__cards {
    grid-template-columns: 1fr;
  }
}
</style>
