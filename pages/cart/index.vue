<template>
  <v-container class="my-md-11 my-8">
    <div
      class="text-capitalize text-center warning--text"
      v-if="$store.state.cart.length == 0"
    >
      <v-img class="d-block mx-auto" src="/emptycart.svg" width="400"></v-img>
      <p class="text-h4">No Items Just Yet keep shoping</p>
    </div>
    <v-row v-else>
      <div>
        <v-btn
          class="text-uppercase"
          nuxt
          to="/cart/confirm"
          min-width="150"
          min-height="45"
          color="primary"
        >
          checkout
        </v-btn>
      </div>
      <template v-for="(item, index) in $store.state.cart">
        <v-col :key="index">
          <v-card color="surface" flat>
            <v-btn
              absolute
              top
              right
              icon
              @click="$store.commit('RemoveCartItem', index)"
            >
              <v-icon>mdi-delete</v-icon>
            </v-btn>
            <v-row dense>
              <v-col md="3">
                <v-img
                  class="rounded-lg"
                  height="220"
                  :src="item.product.image"
                ></v-img>
              </v-col>
              <v-col class="pl-5 pt-2" md="9">
                <h2 class="text-md-h6 font-weight-bold">
                  {{ item.product.name }} x {{ item.quantity }}
                </h2>
                <p class="primary--text mt-2">
                  {{ $formatMoney(item.product.price * item.quantity) }}
                </p>
                <v-btn @click="$store.commit('IncreaseItemCount', index)" icon>
                  <v-icon size="20">mdi-plus-circle</v-icon>
                </v-btn>
                <span class="mx-2">{{ item.quantity }}</span>
                <v-btn @click="$store.commit('DecreaseItemCount', index)" icon>
                  <v-icon size="20">mdi-minus-circle</v-icon>
                </v-btn>
              </v-col>
            </v-row>
          </v-card>
        </v-col>
      </template>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: "cart",
};
</script>
