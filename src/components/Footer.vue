<template>
  <footer class="game-footer">
    <div class="game-footer__content container">
      <p>&copy; 2026 Polska Husaria. Wszelkie prawa zastrzeżone.</p>
      <p class="game-footer__disclaimer">
        Ta strona nie jest powiązana z Supercell, nie jest przez nich
        sponsorowana ani wspierana.
      </p>
    </div>
  </footer>
</template>

<style lang="scss" scoped>
.game-footer {
  background-color: #050505;
  border-top: 2px solid #261e16;
  padding: 30px 20px;
  text-align: center;
  font-size: 0.9rem;
  color: $fontColor;

  &__content {
    display: flex;
    flex-direction: column;
    gap: 8px;
  }

  &__disclaimer {
    font-size: 0.75rem;
    opacity: 0.6;
  }
}
</style>
