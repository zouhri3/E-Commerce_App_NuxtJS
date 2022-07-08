<template>
  <v-container class="my-md-11 my-8">
    <v-row>
      <v-col md="3">
        <div>
          <v-text-field
            outlined
            placeholder="Search"
            clearable
            prepend-inner-icon="mdi-magnify"
            v-model="search"
          ></v-text-field>
          <v-list>
            <v-subheader class="text-uppercase">categories</v-subheader>
            <v-list-item v-for="(item, index) in categories" :key="index" link>
              <v-list-item-avatar>
                <v-img :src="item.image"></v-img>
              </v-list-item-avatar>
              <v-list-item-content>
                <v-list-item-title>{{ item.name }}</v-list-item-title>
              </v-list-item-content>
            </v-list-item>
          </v-list>
        </div>
      </v-col>

      <v-col md="9">
        <v-row>
          <v-col
            v-for="(item, index) in productsWithSearch"
            :key="index"
            cols="12"
            md="6"
          >
            <v-card
              link
              color="surface"
              class="ma-2 mb-5 mr-5"
              nuxt
              :to="`/products/${item.id}`"
            >
              <v-img :src="item.image" height="300">
                <template #placeholder>
                  <v-row fill-height justify="center" align="center">
                    <v-progress-circular
                      width="2"
                      size="100"
                      color="primary"
                      indeterminate
                    >
                    </v-progress-circular>
                  </v-row>
                </template>
              </v-img>

              <v-card-title class="text-md-body-1 font-weight-bold">{{
                item.name
              }}</v-card-title>
              <v-card-subtitle class="warning--text py-0 pb-3">{{
                $formatMoney(item.price)
              }}</v-card-subtitle>
              <v-card-text>
                <v-chip
                  x-small
                  outlined
                  class="mr-1"
                  label
                  v-for="(chip, index) in item.tags"
                  :key="index"
                >
                  {{ chip }}
                </v-chip>
              </v-card-text>
            </v-card>
          </v-col>
        </v-row>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: "products",

  async created() {
    this.categories = await this.$content("category").fetch();
    this.products = await this.$content("products").fetch();
  },

  data() {
    return {
      categories: Array,
      products: Array,
      search: null,
    };
  },

  computed: {
    productsWithSearch: function () {
      if (!this.search || !this.products) return this.products || [];

      return this.products.filter((item) => {
        const patern = new RegExp(this.search, "i");

        return item.name.match(patern) || item.price.toString().match(patern);
      });
    },
  },
};
</script>