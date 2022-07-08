<template>
  <main>
    <div class="d-flex justify-center" v-if="error.statusCode === 404">
      <v-card class="pa-8 text-center text-capitalize my-12" width="600px">
        <h1 class="text-uppercase mb-3 error--text">
          {{ titleEror }}
        </h1>
        <p>{{ pageNotFound }}</p>
        <p class="error--text">error: {{ error.message }}</p>
        <v-btn color="success" nuxt to="/">go home</v-btn>
      </v-card>
    </div>

    <h1 v-else>
      {{ otherError }}
    </h1>
  </main>
</template>

<script>
export default {
  name: "ErrorLayout",

  props: {
    error: {
      type: Object,
      default: null,
    },
  },
  data() {
    return {
      titleEror: "o-o-o-p-s",
      pageNotFound: "something went wrong here ... :)",
      otherError: "An error occurred",
    };
  },
  head() {
    const title =
      this.error.statusCode === 404 ? this.pageNotFound : this.otherError;
    return {
      title,
    };
  },
};
</script>

<style scoped>
h1 {
  font-size: 20px;
}
.main_div {
  line-height: 100vh;
}
</style>
