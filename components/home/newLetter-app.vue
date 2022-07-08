<template>
  <v-card class="my-md-11 my-8 text-center py-md-10 py-8 primary" flat>
    <v-container>
      <v-card-title
        class="text-md-h3 text-h5 font-weight-bold text-capitalize d-block"
      >
        new letter
      </v-card-title>
      <v-card-subtitle class="text-md-h6 mt-3 text-capitalize"
        >subbscribe to recieve dicounts & more!</v-card-subtitle
      >
      <v-sparkline />
      <v-sheet color="transparent" class="mx-auto" max-width="400">
        <v-form v-model="valid" @click.prevent="validate">
          <v-text-field
            label="E-mail"
            type="email"
            outlined
            v-model="email"
            :rules="emailValid"
            required
            color="bg"
          ></v-text-field>

          <v-btn
            outlined
            min-height="50"
            :disabled="!valid"
            @click="submit()"
            width="100%"
            class="d-block"
            >subscribe</v-btn
          >
        </v-form>
      </v-sheet>
    </v-container>
  </v-card>
</template>

<script>
export default {
  name: "new-letter",
  data() {
    return {
      valid: true,
      email: null,
      emailValid: [
        (v) => !!v || "E-mail is required",
        (v) => /.+@.+/.test(v) || "E-mail must be valid",
      ],
    };
  },
  methods: {
    async submit() {
      await this.$swal({
        title: "Thank You For Subscribing",
        icon: "success",
        allowOutsideClick: false,
        allowEscapekey: false,
        timer: 2000,
        timerProgressbar: true,
        showConfirmButton: false,
        text: "You Will Be Notified When We Have a Deal Or Items On Sale",
      });
    },
  },
};
</script>

<style>
</style>