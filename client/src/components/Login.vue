<template>
  <v-layout column>
    <v-container>
      <v-flex xs6 md6 offset-xs3>
        <div class="white elevation-2">
          <v-toolbar flat dense class="cyan" dark>
            <v-toolbar-title>
              Login
            </v-toolbar-title>
          </v-toolbar>
          <div class="pl-4 pr-4 pt-2 pb-2">
            <form name="tabtracker-registration" autocomplete="off">
              <v-text-field
                label="Email"
                type="email"
                v-model="email">
              </v-text-field>
              <v-text-field
                label="Password"
                type="password"
                v-model="password">
              </v-text-field>
              <v-btn @click="login" class="cyan" dark>Login</v-btn>
            </form>
            <br>
            <div class="error-mssg" v-html="error"></div>
          </div>
        </div>
      </v-flex>
    </v-container>
  </v-layout>
</template>
<script>
import AuthenticationService from '@/services/AuthenticationService'
export default {
  data () {
    return {
      email: '',
      password: '',
      error: ''
    }
  },
  methods: {
    async login () {
      try {
        const response = await AuthenticationService.login({
          email: this.email,
          password: this.password
        })
        console.log(response)
        this.$store.dispatch('setToken', response.data.token)
        this.$store.dispatch('setUser', response.data.user)
        this.error = null
      } catch (err) {
        console.log(err.response)
        this.error = err.response.data.error
      }
      // console.log(response.data)
    }
  }
}
</script>
<style scoped>
.error-mssg{
  color: red;
}
</style>
