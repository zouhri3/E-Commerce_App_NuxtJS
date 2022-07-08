<template>
  <v-container class="my-md-11 my-8">
    <v-row justify="center" v-if="product">
      <v-col md="8" cols="11">
        <v-card class="px-5 py-7">
          <h2 class="text-center text-md-h4">{{ product.name }}</h2>
          <div class="text-center my-3">
            <v-rating
              small
              readonly
              half-increments
              class="mb-2"
              color="yellow darken-2"
              background-color="gray lighten-1"
              :value="product.ratings"
            ></v-rating>
            <v-chip
              small
              outlined
              class="mr-1"
              label
              v-for="(chip, index) in product.tags"
              :key="index"
            >
              {{ chip }}
            </v-chip>
          </div>
          <v-img
            width="100%"
            class="rounded-lg"
            height="50vh"
            :src="product.image"
          >
          </v-img>
          <p class="mt-5 mb-7">{{ product.description }}</p>
          <v-btn
            min-height="45"
            min-width="170"
            color="primary"
            @click="$store.commit('AddToCart', product)"
            >add to cart</v-btn
          >
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  async created() {
    const p = await this.$content("products")
      .where({
        id: parseInt(this.$route.params.id),
      })
      .fetch();
    this.product = p[0];
  },

  data() {
    return {
      product: Array,
    };
  },
};
</script>

