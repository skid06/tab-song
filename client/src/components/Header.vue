<template>
  <v-toolbar fixed class="cyan" dark>
    <v-toolbar-title class="mr-4">
      TabTracker
    </v-toolbar-title>
    <v-toolbar-items>
      <v-btn flat dark>
        Browse
      </v-btn>
    </v-toolbar-items>
    <v-spacer />
    <v-toolbar-items>
      <v-btn flat dark router to="/login">
        Login
      </v-btn>
    </v-toolbar-items>
    <v-toolbar-items>
      <v-btn flat dark router to="/register">
        Sign Up
      </v-btn>
    </v-toolbar-items>
  </v-toolbar>
</template>
<script>

</script>
<style scoped>

</style>
