<script setup>
import Footer from './components/Footer/Footer.vue';
import Header from './components/Header/Header.vue';
import Projects from './components/Projects/Projects.vue';
</script>

<template>
  <Header />
  <main>
    <Projects />
  </main>
  <Footer />
</template>


<style lang="scss">
.sr-only {
  position: absolute;
  width: 1px;
  height: 1px;
  padding: 0;
  margin: -1px;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  white-space: nowrap;
  border-width: 0;
}

:root {
  --size-1: 0.25rem;
  --size-2: 0.5rem;
  --size-3: 0.75rem;
  --size-4: 1rem;
  --size-5: 1.25rem;
  --size-6: 1.5rem;
  --size-7: 1.75rem;
  --size-8: 2rem;
  --size-9: 2.25rem;
  --size-10: 2.5rem;
  --size-11: 2.75rem;
  --size-12: 3rem;
  --size-13: 3.25rem;
  --size-14: 3.5rem;
  --size-15: 3.75rem;
  --size-16: 4rem;
  --size-17: 4.25rem;
  --size-18: 4.5rem;
  --size-19: 4.75rem;
  --size-20: 5rem;
  --size-21: 5.25rem;
  --size-22: 5.5rem;
  --size-23: 5.75rem;
  --size-24: 6rem;
  --size-25: 6.25rem;
  --size-26: 6.5rem;
  --size-27: 6.75rem;
  --size-28: 7rem;
  --size-29: 7.25rem;
  --size-30: 7.5rem;
  --size-31: 7.75rem;
  --size-32: 8rem;
  --size-33: 8.25rem;
  --size-34: 8.5rem;
  --size-35: 8.75rem;
  --size-36: 9rem;
}

.container {
  --max-width:1120px;
  width: min(calc(100% - 4rem), var(--max-width));
  margin-inline: auto;

  &--large{
    --max-width:1368px;
  }

}

body {
  font-family: "Barlow", system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
}
</style>