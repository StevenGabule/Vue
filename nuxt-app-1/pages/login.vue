<template>
  <v-form @submit.prevent="submit" ref="form" lazy-validation>
    <v-text-field
      v-model="form.email"
      label="E-mail"
      required
    ></v-text-field>

    <v-text-field
      type="password"
      v-model="form.password"
      label="Password"
      required
    ></v-text-field>
    <v-btn type="submit" color="primary"> Login </v-btn>
  </v-form>
</template>

<script>
export default {
  name: "Login",
  data() {
    return {
      form: {
        email: "person@gmail.com",
        password: "password",
      }
    }
  },
  methods: {
    async submit() {
      try {
        let response = await this.$auth.loginWith('local', {
          data: this.form
        })
        console.log("::submit::", response.user)
        console.log("::token::", response.token)
      } catch (error) {
        console.log(error);
      }
    }
  }
};
</script>
