<template>
  <v-layout justify-center align-center>
    <v-flex>
      <!-- <adsense
        :ad-client="adClient"
        :ad-slot="adSlot"
        ad-style="display: block"
        ad-format="auto">
      </adsense> -->
    </v-flex>
  </v-layout>
</template>

<script>
import VueAdsense from './VueAdsense.vue'

export default {
  name: 'adsComponent',
  data () {
    return {
      adClient: process.env.ADSENSE_AD_CLIENT,
      adSlot: process.env.ADSENSE_AD_SLOT
    }
  },
  components: {
    'adsense': VueAdsense
  }
}
</script>
