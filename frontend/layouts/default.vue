<template>
<v-app id="tipgv" toolbar footer>
  <v-toolbar class="primary" dark>
    <div class="layout-logo-center">
      <a :href="baseUrl" :title="siteName">
        <img src="~/assets/logo/logo.png" width="40" height="40" :alt="siteName">
      </a>
    </div>
    <v-toolbar-title>{{ siteName }}</v-toolbar-title>
    <v-toolbar-side-icon @click.stop="drawer = !drawer"></v-toolbar-side-icon>
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
  methods: {
    toggleClick () {
      if (this.spanLeft === 5) {
        this.spanLeft = 2
        this.spanRight = 22
      } else {
        this.spanLeft = 5
        this.spanRight = 19
      }
    }
  },
  components: {
    'footer-component': Footer,
    'header-component': Header
  }
}
</script>

<style>
.layout {
  border: 1px solid #d7dde4;
  background: #f5f7f9;
  position: relative;
  border-radius: 4px;
  overflow: hidden;
}

.layout-content {
  min-height: 200px;
  margin: 15px;
  overflow: hidden;
  background: #fff;
  border-radius: 4px;
}

.layout-content-main {
  padding: 40px;
}

.layout-hide-text .layout-text {
  display: none;
}

.layout-header {
  height: 60px;
  background: #fff;
  box-shadow: 0 1px 1px rgba(0,0,0,.1);
}

a {
  color: #de47ac;
}

a:hover {
  color: #cb60b3;
}
</style>