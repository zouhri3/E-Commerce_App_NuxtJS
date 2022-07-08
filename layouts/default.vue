<template>
  <v-app dark>
    <nav-app />

    <v-main>
      <Nuxt />
    </v-main>

    <button-scroll-top-app />

    <footer-app />
  </v-app>
</template>

<script>
import FooterApp from "~/components/footer-app.vue";
import ButtonScrollTopApp from "~/components/home/buttonScrollTop-app.vue";
import navApp from "~/components/nav-app.vue";

export default {
  components: { navApp, FooterApp, ButtonScrollTopApp },
  name: "DefaultLayout",
};
</script>
