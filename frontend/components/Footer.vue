<template>
    <footer>
        <v-footer class="pa-3 primary">
            <v-spacer></v-spacer>
            <p class="text-lg-right text-xl-right">
                <a :href="baseUrl">
                    <img src="~/assets/logo/logo.png" :alt="siteName" width="40" height="40">
                </a> | 
                <a :href="'https://twitter.com/' + twHandle"><i class="fa fa-twitter"></i></a>&nbsp;
                <a :href="'https://www.facebook.com/' + fbHandle"><i class="fa fa-facebook"></i></a></p> | 
                &copy; {{ new Date().getFullYear() }} <a :href="baseUrl">{{ siteName }}</a> | 
                Developed by <a href="https://talaikis.com">Talaikis Inc.</a>
            </p>
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
.align-center {
    text-align: center;
    font-size: 0.8em;
    padding: 5em 0 5em 0;
    color: #9ea7b4;
  }
</style>