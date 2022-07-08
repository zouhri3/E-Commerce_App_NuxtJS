<template>
  <v-card>
    <v-footer class="pa-0 surface">
      <v-container>
        <v-card
          tile
          color="surface"
          flat
          class="pa-md-10 pa-5 text-center"
          width="100%"
        >
          <v-card-title
            class="
              text-md-h5
              font-weight-bold
              pointer
              d-flex
              justify-center
              align-center
            "
          >
            <v-btn @click="$router.push('/')" depressed color="surface"
              >e-commerce</v-btn
            >
          </v-card-title>
          <v-card-text>
            <v-btn icon v-for="(icon, index) in sm" :key="index" fab depressed>
              <v-icon size="20">{{ icon.icon }}</v-icon>
            </v-btn>
          </v-card-text>
        </v-card>
      </v-container>
    </v-footer>
  </v-card>
</template>

<script>
export default {
  data() {
    return {
      sm: [
        {
          icon: "mdi-facebook",
          link: "#",
        },
        {
          icon: "mdi-twitter",
          link: "#",
        },
        {
          icon: "mdi-instagram",
          link: "#",
        },
        {
          icon: "mdi-youtube",
          link: "#",
        },
      ],
    };
  },
};
</script>

<style>
</style>