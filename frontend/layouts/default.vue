<template>
<v-app id="tipgv" toolbar footer>
  <v-container :fluid="true">
  <v-toolbar class="primary" dark>
    <div class="layout-logo-center">
      <a :href="baseUrl" :title="siteName">
        <img src="~/assets/logo/logo.png" width="40" height="40" :alt="siteName">
      </a>
    </div>
    <v-toolbar-title>{{ siteName }}</v-toolbar-title>
    <header-component :spanLeft="spanLeft"></header-component>
    <v-spacer></v-spacer>
    <v-btn icon>
      <v-icon>fa fa-facebook fw</v-icon>
    </v-btn>
    <v-btn icon>
      <v-icon>fa fa-twitter fw</v-icon>
    </v-btn>
  </v-toolbar>
  <main>
      <v-container fluid>
        <nuxt/>
      </v-container>
  </main>
  <v-footer class="primary">
    <footer-component></footer-component>
  </v-footer>
  </v-container>
</v-app>
</template>

<script>
import Footer from '../components/Footer.vue'
import Header from '../components/Header.vue'

export default {
  name: 'mainLayout',
  data () {
    return {
      spanLeft: 5,
      spanRight: 19,
      siteName: process.env.SITE_NAME,
      baseUrl: process.env.BASE_URL
    }
  },
  components: {
    'footer-component': Footer,
    'header-component': Header
  }
}
</script>

<style>
</style>