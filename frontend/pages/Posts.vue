<template>
<div>
  <ad-component></ad-component>
  <v-layout row wrap v-for="(chunk, index) in chunkPosts" :key="'p-' + index" class="posts-row">
    <v-flex xs12 sm8 md6 pa-1 v-for="(post, i) in chunk" :key="index + i">
      <v-card>
        <a :href="baseUrl + post.slug + '/'" v-if="post.image">
          <v-card-media :src="imgBaseUrl + post.image" height="200px">
          </v-card-media>
        </a>
        <div class="pa-5">
          <v-card-title primary-title>
            <h3 class="display-1">
              <a :href="baseUrl + post.slug + '/'">{{ post.title }}</a>
            </h3>
          </v-card-title>
          <div>
            <p><small>
              <a :href="baseUrl + keyword + '/' + post.category_id.Slug + '/'">{{ post.category_id.Title }}</a>
              | {{ post.date | formatDate }}
            </small></p>
          </div>
          <div>
            <p v-if="post.content" class="subheading">{{ post.content | truncate }}</p>
          </div>
          <v-card-actions>
            <v-btn flat info>
              <a :href="baseUrl + keyword + '/' + post.category_id.Slug + '/'">
                Read more...
              </a>
            </v-btn>
          </v-card-actions>
        </div>
      </v-card>
    </v-flex>
    <div xs12 sm12 md12 lg12 xl12 v-if="index === (3 || 7)">
      <ad-component></ad-component>
    </div>
    </v-layout>
  </v-layout>
  <paginator-component v-once :totalPages="calcPages" :paginatorType="paginatorType" value="" :currentPage="page" :itemsPerPage="itemsPerPage" :totalItems="posts[0].total_posts">
  </paginator-component>
</div>
</template>

<script>
import chunk from '../plugins/chunk'
import Paginator from '../components/Paginator.vue'
import Ads from '../components/Ads.vue'
import axios from 'axios'

export default {
  data () {
    return {
      posts: [],
      baseUrl: process.env.BASE_URL,
      imgBaseUrl: process.env.IMG_URL,
      title: process.env.SITE_NAME,
      keyword: process.env.KEYWORD,
      page: null,
      paginatorType: 0,
      itemsPerPage: 20
    }
  },
  asyncData ({ req, params, error }) {
    return axios.get('/posts/' + (Number(params.page) || '0') + '/')
      .then((response) => {
        return { posts: response.data, page: Number(params.page) || 0 }
      })
      .catch((e) => {
        error({ statusCode: 500, message: e })
      })
  },
  components: {
    'paginator-component': Paginator,
    'ad-component': Ads
  },
  computed: {
    chunkPosts () {
      return chunk(this.posts, 2)
    },
    calcPages () {
      const pages = Math.floor(this.posts[0].total_posts / 20)
      return pages <= 250 ? pages : 250
    }
  },
  head () {
    return {
      title: Number(this.$route.params.page) ? 'Page ' + Number(this.$route.params.page) + ' | ' + this.title : this.title
    }
  }
}
</script>

<style>
</style>
