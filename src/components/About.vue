<script setup>
import { ref, onMounted } from "vue";

// Rozbudowana lista ofert z rombami
const offers = [
  {
    label: "Wojny i Ligi Wojen",
    text: "Dla chętnych ciągłe CW / CWL.",
  },
  {
    label: "Weekendowe Raidy",
    text: "Wspólne czyszczenie dystryktów w Capital Peak i stały dopływ Raid Medals.",
  },
  {
    label: "Gry Klanowe",
    text: "Zawsze maksymalne nagrody w Clan Games.",
  },
  {
    label: "Wsparcie Taktyczne",
    text: "Pomoc w projektowaniu baz, dobieraniu armii i planowaniu skomplikowanych ataków.",
  },
  {
    label: "Zaplecze Wojskowe",
    text: "Błyskawiczne donacje wysokopoziomowych jednostek, maszyn oblężniczych oraz czarów.",
  },
  {
    label: "Stabilna Społeczność",
    text: "Dojrzałe środowisko bez toksyczności, nastawione na długofalową i wspólną zabawę.",
  },
];

// Rozbudowana lista oczekiwań z rombami
const requirements = [
  {
    label: "No rush",
    text: "Stawiamy na solidnie rozwinięte wioski, bohaterów i mury przed przejściem na wyższe TH.",
  },
  {
    label: "Odpowiedzialność",
    text: "Zgłoszeni uczestnicy zobowiązani są do wykorzystania obu ataków w wojnie.",
  },
  {
    label: "Komunikacja",
    text: "Obecność na naszym klanowym czacie lub serwerze Discord w celu sprawnej koordynacji.",
  },
  {
    label: "Aktywność w grach",
    text: "Wymagamy minimalnego zaangażowania punktowego podczas comiesięcznych Clan Games.",
  },
  {
    label: "Kultura osobista",
    text: "Szanujemy swój czas i siebie nawzajem – brak dramatów, toxic zachowań i wyzwisk.",
  },
];

const mainTitle = ref(null);
const leftCard = ref(null);
const rightCard = ref(null);

onMounted(() => {
  const observerOptions = {
    root: null,
    threshold: 0.1,
  };

  const observer = new IntersectionObserver((entries) => {
    entries.forEach((entry) => {
      if (entry.isIntersecting) {
        entry.target.classList.add("is-visible");
      } else {
        entry.target.classList.remove("is-visible");
      }
    });
  }, observerOptions);

  if (mainTitle.value) observer.observe(mainTitle.value);
  if (leftCard.value) observer.observe(leftCard.value);
  if (rightCard.value) observer.observe(rightCard.value);
});
</script>

<template>
  <section class="about-section container">
    <h2 ref="mainTitle" class="about-section__main-title">O nas</h2>

    <div class="about-section__grid">
      <!-- Co oferujemy (Wjazd z lewej) -->
      <div ref="leftCard" class="about-card about-card--left">
        <h3 class="about-card__title">⚔️ Co oferujemy? ⚔️</h3>
        <ul class="about-card__list">
          <li
            v-for="(offer, idx) in offers"
            :key="idx"
            class="about-card__item about-card__item--column"
            :style="{ '--item-idx': idx }"
          >
            <strong>🔸 {{ offer.label }}:</strong>
            <span class="desc">{{ offer.text }}</span>
          </li>
        </ul>
      </div>

      <!-- Czego oczekujemy (Wjazd z prawej) -->
      <div ref="rightCard" class="about-card about-card--alt about-card--right">
        <h3 class="about-card__title">🛡️ Czego oczekujemy? 🛡️</h3>
        <ul class="about-card__list">
          <li
            v-for="(req, idx) in requirements"
            :key="idx"
            class="about-card__item about-card__item--column"
            :style="{ '--item-idx': idx }"
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
  &__main-title {
    font-family: $headerFont;
    color: #e6e2de;
    font-size: 3rem;
    text-align: center;
    text-transform: uppercase;
    letter-spacing: 4px;
    margin-bottom: 60px;
    position: relative;

    opacity: 0;
    transform: translateY(-50px);
    will-change: transform, opacity;
    transition:
      transform 0.8s cubic-bezier(0.16, 1, 0.3, 1),
      opacity 0.6s ease;

    &::after {
      content: "";
      position: absolute;
      bottom: -15px;
      left: 50%;
      transform: translateX(-50%);
      width: 80px;
      height: 3px;
      background-color: $primaryColor;
    }

    &.is-visible {
      opacity: 1;
      transform: translateY(0);
    }
  }

  &__grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 40px;
    overflow: hidden;
    padding: 10px;
  }
}

.about-card {
  background-color: $backgroundColor;
  border: $borderGame;
  border-radius: 6px;
  padding: 40px;
  -webkit-box-shadow: 0px 0px 10px 5px rgba(0, 0, 0, 0.56);
  box-shadow: 0px 0px 10px 5px rgba(0, 0, 0, 0.56);

  opacity: 0;
  will-change: transform, opacity;
  transition:
    transform 0.9s cubic-bezier(0.16, 1, 0.3, 1),
    opacity 0.7s ease;

  &--left {
    transform: translateX(-100px);
  }

  &--right {
    transform: translateX(100px);
  }

  &.is-visible {
    opacity: 1;
    transform: translateX(0);

    .about-card__item {
      opacity: 1;
      transform: translateY(0);
      // Animacja kaskadowa automatycznie przeliczy się dla wszystkich 5 elementów!
      transition-delay: calc((var(--item-idx) * 0.12s) + 0.25s);
    }
  }

  &--alt {
    border-color: $redColor;
    // box-shadow:
    //   0 15px 35px rgba(0, 0, 0, 0.4),
    //   0 0 20px rgba($redColor, 0.1);
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
    margin-bottom: 22px; // Delikatnie zwiększony margines dla lepszej czytelności przy 5 elementach
    color: $fontColor;
    display: flex;

    opacity: 0;
    transform: translateY(30px);
    will-change: transform, opacity;
    transition:
      transform 0.6s cubic-bezier(0.16, 1, 0.3, 1),
      opacity 0.5s ease;
    transition-delay: 0s;

    &:last-child {
      margin-bottom: 0;
    }

    &--column {
      flex-direction: column;
      gap: 4px;

      strong {
        color: $primaryColor;
        font-size: 1.15rem;
        letter-spacing: 0.5px;
      }
      .desc {
        color: #b0a8a0;
        padding-left: 28px;
      }
    }
  }
}

@media (max-width: 992px) {
  .about-section {
    &__main-title {
      font-size: 2.2rem;
      margin-bottom: 40px;
      transform: translateY(-30px);
    }

    &__grid {
      grid-template-columns: 1fr;
      gap: 30px;
    }
  }

  .about-card {
    &--left {
      transform: translateX(-40px);
    }
    &--right {
      transform: translateX(40px);
    }

    &__item {
      &--column {
        .desc {
          padding-left: 0;
        }
      }
    }
  }
}
</style>
