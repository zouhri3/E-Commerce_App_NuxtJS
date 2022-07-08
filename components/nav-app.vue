<template>
  <v-app-bar color="surface" height="80px" app>
    <v-container class="d-flex">
      <v-toolbar-title
        class="text-md-h5 font-weight-bold pointer d-flex align-center"
      >
        <v-btn @click="$router.push('/')" depressed color="surface"
          >e-commerce</v-btn
        >
      </v-toolbar-title>

      <v-spacer />

      <v-btn icon nuxt to="/products">
        <v-icon size="20">mdi-store-outline</v-icon>
      </v-btn>
      <v-badge
        v-if="$store.state.cart.length > 0"
        overlap
        :content="`${$store.state.cart.length}`"
      >
        <v-btn icon nuxt to="/cart">
          <v-icon size="20">mdi-cart-outline</v-icon>
        </v-btn>
      </v-badge>
      <v-btn v-else nuxt to="/cart" icon>
        <v-icon size="20">mdi-cart-outline</v-icon>
      </v-btn>
      <v-divider vertical class="mx-md-5 mx-2" />
      <v-btn icon @click="switchMode">
        <v-icon size="20">{{
          light == true ? "mdi-brightness-4" : "mdi-brightness-7"
        }}</v-icon>
      </v-btn>
    </v-container>
  </v-app-bar>
</template>

<script>
export default {
  name: "nav-app",
  data() {
    return {
      light: true,
    };
  },
  methods: {
    switchMode() {
      this.$vuetify.theme.dark = !this.$vuetify.theme.dark;
      this.light = !this.light;
    },
  },
};
</script>

<style>
</style>