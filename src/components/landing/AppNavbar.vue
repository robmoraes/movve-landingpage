<template>
  <header class="app-navbar">
    <div class="landing-container app-navbar__inner">
      <a
        class="app-navbar__brand"
        href="#hero"
        aria-label="Movve"
        @click.prevent="scrollToSection('hero')"
      >
        <img :src="movveLogo" alt="Movve" class="app-navbar__logo" />
      </a>

      <nav class="app-navbar__links">
        <q-btn
          v-for="item in navigationItems"
          :key="item.id"
          flat
          no-caps
          class="app-navbar__link"
          :label="item.label"
          @click="scrollToSection(item.id)"
        />
      </nav>

      <q-btn flat round dense class="app-navbar__menu" icon="mdi-menu" aria-label="Abrir menu">
        <q-menu anchor="bottom right" self="top right">
          <q-list class="app-navbar__mobile-list">
            <q-item
              v-for="item in navigationItems"
              :key="item.id"
              v-close-popup
              clickable
              @click="scrollToSection(item.id)"
            >
              <q-item-section>{{ item.label }}</q-item-section>
            </q-item>
          </q-list>
        </q-menu>
      </q-btn>
    </div>
  </header>
</template>

<script setup>
import movveLogo from 'assets/branding/logo/movve-wordmark.svg'

const navigationItems = [
  { label: 'Sobre', id: 'sobre' },
  { label: 'O que fazemos', id: 'o-que-fazemos' },
  { label: 'Como funciona', id: 'como-funciona' },
  { label: 'Benefícios', id: 'beneficios' },
  { label: 'Diferenciais', id: 'diferenciais' },
  { label: 'Planos', id: 'planos' },
  { label: 'Missão', id: 'missao' },
  { label: 'Contatos', id: 'contatos' },
]

function scrollToSection(id) {
  document.getElementById(id)?.scrollIntoView({ behavior: 'smooth', block: 'start' })
}
</script>

<style lang="scss" scoped>
.app-navbar {
  position: fixed;
  inset: 0 0 auto;
  z-index: 1000;
  background: rgba(255, 255, 255, 0.94);
  border-bottom: 1px solid rgba(4, 50, 113, 0.1);
  backdrop-filter: blur(12px);
}

.app-navbar__inner {
  min-height: 72px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 24px;
}

.app-navbar__brand {
  display: inline-flex;
  align-items: center;
  flex: 0 0 auto;
  line-height: 0;
}

.app-navbar__logo {
  display: block;
  width: clamp(112px, 14vw, 150px);
  height: auto;
}

.app-navbar__links {
  display: flex;
  align-items: center;
  gap: 2px;
}

.app-navbar__link {
  color: var(--movve-blue);
  font-weight: 600;
}

.app-navbar__menu {
  display: none;
  color: var(--movve-blue);
}

.app-navbar__mobile-list {
  min-width: 220px;
  color: var(--movve-blue);
}

@media (max-width: 920px) {
  .app-navbar__links {
    display: none;
  }

  .app-navbar__menu {
    display: inline-flex;
  }
}
</style>
