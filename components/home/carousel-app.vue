<template>
  <v-carousel
    show-arrows-on-hover
    hide-delimiter-background
    :height="carousel_height()"
    cycle
    interval="6000"
  >
    <v-carousel-item v-for="(slide, i) in slides" :key="i">
      <v-img :src="slide.image" height="100%">
        <v-container class="fill-height">
          <v-row dense align="center">
            <v-col md="7">
              <v-card
                color="transparent"
                class="
                  pa-md-10 pa-5
                  rounded-lg
                  text-center text-md-left
                  relative
                "
              >
                <div class="overlay over_lay"></div>
                <v-card-title class="text-md-h3 text-h5 d-block">{{
                  slide.name
                }}</v-card-title>
                <v-card-subtitle
                  class="text-md-h3 text-subtitle-1 primary--text mt-5"
                >
                  {{ $formatMoney(slide.price) }}
                </v-card-subtitle>
                <v-card-text>
                  {{ slide.description }}
                </v-card-text>
                <v-card-actions>
                  <v-btn
                    depressed
                    color="primary"
                    class="text-capitalize mx-auto mx-md-0"
                    min-height="40"
                    nuxt
                    :to="`/products/${slide.id}`"
                  >
                    check it out
                  </v-btn>
                </v-card-actions>
              </v-card>
            </v-col>
          </v-row>
        </v-container>
      </v-img>
    </v-carousel-item>
  </v-carousel>
</template>

<script>
export default {
  name: "carousel-main",
  props: {
    slides: Array,
  },
  data() {
    return {
      modeTheme: this.$vuetify.theme.dark,
    };
  },
  methods: {
    carousel_height() {
      const Height = window.innerHeight;
      return Height - 80;
    },
  },
};
</script>

<style lang="scss">
.overlay {
  position: absolute;
  width: 100%;
  height: 100%;
  left: 0;
  z-index: -1;
  top: 0;
  opacity: 0.7;
}
</style>