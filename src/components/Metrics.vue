<script setup>
const clans = [
  {
    type: "Klan Główny",
    name: "Polska Husaria",
    tag: "#2YRL8C2Q2",
    icon: "🛡️",
    stats: { level: 18, warWins: 420, cwl: "Masters I" },
  },
  {
    type: "Akademia",
    name: "Polska KropIAK",
    tag: "#2G0UV8RGC",
    icon: "📖",
    stats: { level: 10, warWins: 150, cwl: "Crystal II" },
  },
  {
    type: "CW podczas CWL",
    name: "Liga Dobra",
    tag: "#2YRL8C2Q2",
    icon: "💀",
    stats: { level: 12, warWins: 198, cwl: "Masters III" },
  },
];
</script>

<template>
  <section class="metrics-section container">
    <div class="metrics-section__header">
      <h2 class="metrics-section__title">⚜️ Rodzina Klanów ⚜️</h2>
      <p class="metrics-section__subtitle">
        Nasze dywizje i aktualne osiągnięcia w uniwersum Clash of Clans
      </p>
    </div>

    <div class="metrics-section__grid">
      <div v-for="(clan, idx) in clans" :key="idx" class="clan-card">
        <div class="clan-card__badge">{{ clan.type }}</div>

        <div class="clan-card__main">
          <div class="clan-card__icon">{{ clan.icon }}</div>
          <div class="clan-card__info">
            <h3 class="clan-card__name">{{ clan.name }}</h3>
            <span class="clan-card__tag">Tag: {{ clan.tag }}</span>
          </div>
        </div>

        <div class="clan-card__stats">
          <div class="stat-item">
            <span class="stat-item__label">Poziom</span>
            <span class="stat-item__value">{{ clan.stats.level }}</span>
          </div>
          <div class="stat-item">
            <span class="stat-item__label">Wygrane Wojny</span>
            <span class="stat-item__value">{{ clan.stats.warWins }}</span>
          </div>
          <div class="stat-item">
            <span class="stat-item__label">Liga CWL</span>
            <span class="stat-item__value stat-item__value--gold">{{
              clan.stats.cwl
            }}</span>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style lang="scss" scoped>
.metrics-section {
  padding: 60px 20px 100px 20px;

  &__header {
    text-align: center;
    margin-bottom: 50px;
  }

  &__title {
    font-family: $headerFont;
    color: $primaryColor;
    font-size: 2.5rem;
    margin-bottom: 10px;
  }

  &__subtitle {
    color: $fontColor;
    font-size: 1.1rem;
  }

  &__grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
    gap: 30px;
  }
}

.clan-card {
  background: linear-gradient(
    135deg,
    $backgroundColor 0%,
    $supportLightColor 100%
  );
  border: $borderGame;
  border-radius: 6px;
  padding: 24px;
  box-shadow: $boxShadowHeavy;
  position: relative;

  &__badge {
    position: absolute;
    top: -14px;
    left: 50%;
    transform: translateX(-50%);
    background-color: $redColor;
    border: 1px solid $primaryColor;
    padding: 4px 16px;
    font-family: $headerFont;
    font-size: 0.85rem;
    font-weight: bold;
    letter-spacing: 1px;
    text-transform: uppercase;
    white-space: nowrap;
  }

  &__main {
    display: flex;
    align-items: center;
    gap: 16px;
    margin-top: 10px;
    margin-bottom: 24px;
    padding-bottom: 16px;
    border-bottom: 1px solid rgba($primaryColor, 0.2);
  }

  &__icon {
    font-size: 2.5rem;
  }

  &__name {
    margin: 0 0 4px 0;
    font-family: $headerFont;
    font-size: 1.4rem;
    color: $fontColor;
  }

  &__tag {
    font-size: 0.9rem;
    color: $primaryColor;
    font-family: monospace;
  }

  &__stats {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 10px;
    text-align: center;
  }
}

.stat-item {
  &__label {
    display: block;
    font-size: 0.75rem;
    text-transform: uppercase;
    color: $fontColor;
    margin-bottom: 4px;
  }

  &__value {
    font-size: 1.1rem;
    font-weight: bold;
    color: $fontColor;

    &--gold {
      color: $primaryColor;
    }
  }
}
</style>
