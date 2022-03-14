<template>
  <form @submit.prevent="registerSubmit">

    <v-text-field v-model="form.name" label="Name" required></v-text-field>
    <v-text-field v-model="form.email" label="E-mail" required></v-text-field>

    <v-text-field
      type="password"
      v-model="form.password"
      label="Password"
      required
    ></v-text-field>

    <v-text-field
      type="password"
      v-model="form.confirm_password"
      label="Confirm Password"
      required
    ></v-text-field>
    <v-btn type="submit" color="primary"> Register </v-btn>
  </form>
</template>

<script>

export default {
  name: "Register",
  data() {
    return {
      form: {
        name: "",
        email: "",
        password: "",
        confirm_password: "",
      },
    };
  },
  methods: {
    async registerSubmit() {
      const response = await this.$axios.$post('/sign-up', {
        name: this.form.name,
        email: this.form.email,
        password: this.form.password
      })
      console.log("::registerSubmit::", response)
    },
  },
};
</script>
