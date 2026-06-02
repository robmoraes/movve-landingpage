<template>
  <section id="diferenciais" class="differentials-section landing-section">
    <div class="landing-container">
      <div class="differentials-section__grid">
        <q-card flat class="differentials-section__card differentials-section__content-card">
          <q-card-section>
            <h2 class="differentials-section__title">
              Diferenciais
              <span class="text-movve-green">movve</span>
            </h2>

            <q-list class="differentials-section__list">
              <q-item
                v-for="item in items"
                :key="item"
                dense
                class="differentials-section__list-item"
              >
                <q-item-section avatar>
                  <q-icon name="mdi-check-circle" class="text-movve-green" size="24px" />
                </q-item-section>
                <q-item-section>{{ item }}</q-item-section>
              </q-item>
            </q-list>
          </q-card-section>
        </q-card>

        <div class="differentials-section__image-placeholder" aria-label="Ilustração futura">
          <q-icon name="mdi-image-outline" size="54px" class="text-movve-blue" />
          <p>Ilustração dos diferenciais</p>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const items = [
  'Aulas dinâmicas, leves e personalizadas',
  'Metodologia própria e olhar humanizado',
  'Música ambiente que estimula e acolhe',
  'Foco em saúde física, mental e emocional',
  'Mindfulness (atenção plena) para mais equilíbrio e presença',
  'Prevenção de riscos físicos e psicossociais',
  'Experiência que gera bem-estar e resultados reais',
]
</script>

<style lang="scss" scoped>
.differentials-section {
  padding: 104px 0;
  background: var(--movve-light-blue);
}

.differentials-section__grid {
  min-height: 360px;
  display: grid;
  grid-template-columns: minmax(0, 1.35fr) minmax(280px, 0.65fr);
  align-items: center;
  gap: 48px;
}

.differentials-section__title {
  max-width: 620px;
  margin: 0;
  color: var(--movve-blue);
  font-size: clamp(2rem, 4vw, 3.3rem);
  font-weight: 850;
  line-height: 1.08;
}

.differentials-section__card {
  background: transparent;
  border-radius: 8px;
  color: #4b5563;
  font-size: 1.05rem;
  line-height: 1.75;
}

.differentials-section__content-card {
  min-height: 420px;
  display: flex;
  align-items: center;
}

.differentials-section__list {
  display: grid;
  grid-template-columns: 1fr;
  gap: 6px;
  margin-top: 28px;
}

.differentials-section__list-item {
  padding-left: 0;
  color: #233c55;
  font-weight: 700;
}

.differentials-section__image-placeholder {
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

.differentials-section__image-placeholder p {
  max-width: 180px;
  margin: 0;
  font-weight: 700;
  line-height: 1.35;
}

@media (max-width: 760px) {
  .differentials-section {
    padding: 72px 0;
  }

  .differentials-section__grid {
    min-height: 420px;
    grid-template-columns: 1fr;
    gap: 28px;
  }

  .differentials-section__content-card,
  .differentials-section__image-placeholder {
    min-height: auto;
  }

  .differentials-section__image-placeholder {
    display: none;
  }
}
</style>
