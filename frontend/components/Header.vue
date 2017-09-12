<template>
<div>
  <div class="text-xs-center">
    <v-layout row wrap primary>
    <v-menu open-on-hover offset-y>
      <v-btn primary slot="activator">Categories</v-btn>
      <v-list key="1">
        <v-list-tile v-for="(cat, index) in categories" :key="'1-' + index" @click="">
          <v-list-tile-action>
            <v-icon>event</v-icon>
          </v-list-tile-action>
          <v-list-tile-content>
            <v-list-tile-title>
              <a :href="baseUrl + keyword + '/' + cat.slug + '/'">
                {{ cat.title }} [{{ cat.post_count }}]
              </a>
            </v-list-tile-title>
          </v-list-tile-content>
        </v-list-tile>
        <hr />
        <v-list-tile @click="">
          <v-list-tile-action>
            <v-icon>event</v-icon>
          </v-list-tile-action>
          <v-list-tile-content>
            <v-list-tile-title>
              <strong>
                <a :href="baseUrl + catKey + '/1/'">
                  All categories
                </a>
              </strong>
            </v-list-tile-title>
          </v-list-tile-content>
        </v-list-tile>
      </v-list>
    </v-menu>
    <v-menu open-on-hover offset-y>
      <v-btn primary slot="activator">Trending</v-btn>
        <v-list key="2">
          <v-list-tile key="2-0">
            <v-list-tile-action>
              <v-icon>event</v-icon>
            </v-list-tile-action>
            <v-list-tile-content>
              <v-list-tile-title>
                <a :href="baseUrl + searchKey + '/keyword/'">
                  Keyword
                </a>
              </v-list-tile-title>
            </v-list-tile-content>
          </v-list-tile>
        </v-list>
    </v-menu>
    </v-layout>
  </div>
</div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'headerComponent',
  data () {
    return {
      categories: this.categories,
      baseUrl: process.env.BASE_URL,
      logoAlt: process.env.SITE_NAME,
      title: process.env.SITE_NAME,
      keyword: process.env.KEYWORD,
      catKey: process.env.CATEGORIES_KEY,
      searchKey: process.env.SEARCH_KEYWORD,
      twHandle: process.env.TWITTE_HANDLE,
      fbHandle: process.env.FACEBOOK_HANDLE,
      drawer: true
    }
  },
  methods: {
    fetchData () {
      axios.get('/cats/0/').then(response => {
        this.categories = response.data
      }).catch(e => {
        console.log(e)
      })
    }
  },
  computed: {
    iconSize () {
      return this.spanLeft === 5 ? 14 : 24
    }
  },
  props: {
    spanLeft: Number
  },
  mounted () {
    this.fetchData()
  }
}
</script>

<style scoped>
.layout-logo-center {
  width: 90%;
  height: 5em;
  border-radius: 3px;
  display: block;
  margin: 25px auto;
  text-align: center;
  background: transparent;
}

/*.dark {
  background: #cb60b3;
  background: -moz-linear-gradient(-45deg, #cb60b3 0%, #ad1283 50%, #de47ac 100%);
  background: -webkit-linear-gradient(-45deg, #cb60b3 0%,#ad1283 50%,#de47ac 100%);
  background: linear-gradient(135deg, #cb60b3 0%,#ad1283 50%,#de47ac 100%);
}

.layout-menu-left {
  background: #cb60b3;
  background: -moz-linear-gradient(-45deg, #cb60b3 0%, #ad1283 50%, #de47ac 100%);
  background: -webkit-linear-gradient(-45deg, #cb60b3 0%,#ad1283 50%,#de47ac 100%);
  background: linear-gradient(135deg, #cb60b3 0%,#ad1283 50%,#de47ac 100%);
}

.layout-text {
  color: #EDE7F6;
}

a {
  color: #EDE7F6;
}

a:hover {
  color: #de47ac;
}

.divided {
  border-width: 1px;
  border-style: solid;
  border-color: #ff4cff #7986CB #7986CB #7986CB;
}*/
</style>