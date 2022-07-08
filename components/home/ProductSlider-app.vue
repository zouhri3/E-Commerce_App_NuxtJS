<template>
  <div class="my-md-11 my-8">
    <v-container>
      <h2 class="text-md-h3 text-h5 font-weight-bold text-capitalize mb-6">
        check these out
      </h2>
      <v-sheet class="mx-auto rounded-lg" style="border: 1px solid">
        <v-slide-group v-model="model" class="pa-4" center-active show-arrows>
          <v-slide-item
            v-for="(item, index) in products"
            :key="index"
            v-slot="{ active, toggle }"
          >
            <v-card
              background-opacity="0"
              class="ma-4"
              height="300"
              width="300"
              @click="toggle"
              nuxt
              :to="`/products/${item.id}`"
            >
              <v-tooltip top color="info">
                <template v-slot:activator="{ on, attrs }">
                  <v-img
                    v-bind="attrs"
                    v-on="on"
                    :src="item.image"
                    height="300"
                    width="300"
                  >
                  </v-img>
                </template>
                <div class="text-capitalize">
                  click him to know more info
                  <Span class="text-uppercase warning--text">or</Span> bay
                </div>
              </v-tooltip>
            </v-card>
          </v-slide-item>
        </v-slide-group>
      </v-sheet>
    </v-container>
  </div>
</template>

<script>
export default {
  name: "product-slider",
  props: {
    products: Array,
  },
  data() {
    return {
      model: null,
    };
  },
};
</script>
