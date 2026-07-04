<script setup>
import Header from "@/components/Header.vue";
import About from "@/components/About.vue";
import Metrics from "@/components/Metrics.vue";
import Footer from "@/components/Footer.vue";
</script>

<template>
  <div class="landing-layout">
    <Header />
    <main>
      <About />
      <Metrics />
    </main>
    <Footer />
  </div>
</template>
