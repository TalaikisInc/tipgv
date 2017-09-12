<template>
    <footer>
        <v-footer class="pa-3 primary">
            <a :href="baseUrl">
                <img src="~/assets/logo/logo.png" :alt="siteName" width="40" height="40">
            </a>&nbsp;
            <v-spacer></v-spacer>
            <a class="txt" :href="'https://twitter.com/' + twHandle"><i class="fa fa-twitter"></i></a>&nbsp;
            <a class="txt" :href="'https://www.facebook.com/' + fbHandle"><i class="fa fa-facebook"></i></a>&nbsp;
            <span class="txt">&copy; {{ new Date().getFullYear() }}</span>&nbsp;
            <a class="txt" :href="baseUrl">{{ siteName }}</a>&nbsp;
            <span class="txt">|</span>&nbsp;
            <span class="txt">Developed by</span> <a class="txt" href="https://talaikis.com">Talaikis Inc.</a>
        </v-footer>
    </footer>
</template>

<script>
export default {
  name: 'footerComponent',
  data () {
    return {
      baseUrl: process.env.BASE_URL,
      twHandle: process.env.TWITTE_HANDLE,
      fbHandle: process.env.FACEBOOK_HANDLE,
      siteName: process.env.SITE_NAME
    }
  }
}
</script>

<style>
.txt {
    color: white;
}
</style>