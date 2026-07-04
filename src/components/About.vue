<script setup>
const offers = [
  "Dla chętnych aktywne CW, CWL, CG i weekendowe Raidy",
  "Pomoc w dobieraniu strategii",
  "Szybkie donacje",
];

const requirements = [
  {
    label: "No rush",
    text: "Stawiamy na solidnie rozwinięte wioski na swoim poziomie TH.",
  },
  {
    label: "Odpowiedzialność",
    text: "Zielona tarcza = oba ataki w wojnie wykorzystane.",
  },
  {
    label: "Komunikacja",
    text: "Obecność na naszym klanowym czacie lub serwerze Discord.",
  },
];
</script>

<template>
  <section class="about-section container">
    <div class="about-section__grid">
      <!-- Co oferujemy -->
      <div class="about-card">
        <h2 class="about-card__title">⚔️ Co oferujemy? ⚔️</h2>
        <ul class="about-card__list">
          <li
            v-for="(offer, idx) in offers"
            :key="idx"
            class="about-card__item"
          >
            <span class="bullet">🛡️</span> {{ offer }}
          </li>
        </ul>
      </div>

      <!-- Czego oczekujemy -->
      <div class="about-card about-card--alt">
        <h2 class="about-card__title">🛡️ Czego oczekujemy? 🛡️</h2>
        <ul class="about-card__list">
          <li
            v-for="(req, idx) in requirements"
            :key="idx"
            class="about-card__item about-card__item--column"
          >
            <strong>🔸 {{ req.label }}:</strong>
            <span class="desc">{{ req.text }}</span>
          </li>
        </ul>
      </div>
    </div>
  </section>
</template>

<style lang="scss" scoped>
.about-section {
  padding: 80px 20px;

  &__grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 40px;
  }
}

.about-card {
  background-color: $backgroundColor;
  border: $borderGame;
  border-radius: 6px;
  padding: 40px;
  box-shadow: $boxShadowHeavy;

  &--alt {
    border-color: $redColor;
  }

  &__title {
    font-family: $headerFont;
    color: $primaryColor;
    font-size: 1.8rem;
    text-align: center;
    margin-top: 0;
    margin-bottom: 30px;
  }

  &__list {
    list-style: none;
    padding: 0;
    margin: 0;
  }

  &__item {
    font-size: 1.1rem;
    line-height: 1.6;
    margin-bottom: 20px;
    color: $fontColor;
    display: flex;
    gap: 12px;

    .bullet {
      color: $primaryColor;
    }

    &--column {
      flex-direction: column;
      gap: 4px;

      strong {
        color: $primaryColor;
      }
      .desc {
        color: $fontColor;
      }
    }
  }
}

@media (max-width: 992px) {
  .about-section__grid {
    grid-template-columns: 1fr;
    gap: 30px;
  }
}
</style>
