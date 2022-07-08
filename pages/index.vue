<template>
  <div>
    <carousel-app :slides="sale_items" />
    <product-slider-app :products="products" />
    <new-letter-app />
  </div>
</template>

<script>
import carouselApp from "~/components/home/carousel-app.vue";
import NewLetterApp from "~/components/home/newLetter-app.vue";
import ProductSliderApp from "~/components/home/ProductSlider-app.vue";
export default {
  async created() {
    this.sale_items = await this.$content("products")
      .where({ onSale: true })
      .fetch();
    this.products = await this.$content("products").fetch();
  },

  components: { carouselApp, ProductSliderApp, NewLetterApp },
  name: "IndexPage",

  data() {
    return {
      products: null,
      sale_items: null,
    };
  },
};
</script>
