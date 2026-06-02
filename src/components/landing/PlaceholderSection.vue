<template>
  <section :id="id" class="placeholder-section landing-section" :class="backgroundClass">
    <div class="landing-container">
      <div class="placeholder-section__grid">
        <div>
          <h2>{{ title }}</h2>
        </div>

        <q-card flat class="placeholder-section__card">
          <q-card-section>
            <p>
              Texto placeholder para estruturar esta secao da landing page. O conteudo final sera
              definido em uma etapa posterior.
            </p>
            <p>
              Este espaco simula volume visual, hierarquia e respiro para validar a arquitetura
              inicial em telas desktop e mobile.
            </p>
          </q-card-section>
        </q-card>
      </div>
    </div>
  </section>
</template>

<script setup>
import { computed } from 'vue'

const props = defineProps({
  id: {
    type: String,
    required: true,
  },
  title: {
    type: String,
    required: true,
  },
  background: {
    type: String,
    default: 'white',
    validator: (value) => ['white', 'blue', 'green'].includes(value),
  },
})

const backgroundClass = computed(() => ({
  'placeholder-section--blue': props.background === 'blue',
  'placeholder-section--green': props.background === 'green',
}))
</script>

<style lang="scss" scoped>
.placeholder-section {
  padding: 104px 0;
  background: var(--movve-background);
}

.placeholder-section--blue {
  background: var(--movve-light-blue);
}

.placeholder-section--green {
  background: var(--movve-light-green);
}

.placeholder-section__grid {
  min-height: 360px;
  display: grid;
  grid-template-columns: minmax(0, 0.9fr) minmax(320px, 1.1fr);
  align-items: center;
  gap: 48px;
}

h2 {
  max-width: 520px;
  margin: 0;
  color: var(--movve-blue);
  font-size: clamp(2rem, 4vw, 3.3rem);
  font-weight: 850;
  line-height: 1.08;
}

.placeholder-section__card {
  border: 1px solid rgba(4, 50, 113, 0.1);
  border-radius: 8px;
  color: #4b5563;
  font-size: 1.05rem;
  line-height: 1.75;
}

.placeholder-section__card p {
  margin: 0;
}

.placeholder-section__card p + p {
  margin-top: 18px;
}

@media (max-width: 760px) {
  .placeholder-section {
    padding: 72px 0;
  }

  .placeholder-section__grid {
    min-height: 420px;
    grid-template-columns: 1fr;
    gap: 28px;
  }
}
</style>
