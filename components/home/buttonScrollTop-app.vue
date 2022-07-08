<template>
  <v-fab-transition>
    <v-btn
      fixed
      fab
      color="warning"
      bottom
      right
      v-scroll="checkScroll"
      v-show="showfab"
      @click="goUp"
    >
      <v-icon>mdi-chevron-up</v-icon>
    </v-btn>
  </v-fab-transition>
</template>

<script>
export default {
  name: "scroll-top-app",
  data() {
    return {
      showfab: false,
    };
  },
  methods: {
    checkScroll() {
      window.scrollY > window.innerHeight - 150
        ? (this.showfab = true)
        : (this.showfab = false);
    },
    goUp() {
      this.$vuetify.goTo(0, {
        duration: 1000,
      });
    },
  },
};
</script> 