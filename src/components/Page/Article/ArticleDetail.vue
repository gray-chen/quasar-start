<template>
  <!-- if you want automatic padding use "layout-padding" class -->
  <div class="layout-padding">
    <!-- your content -->
    <div v-if="edit_mode">
      <q-input v-model="article.title" float-label="Title" placeholder="Title" />
      <q-input
        v-model="article.content"
        type="textarea"
        float-label="Textarea"
        :max-height="100"
        :min-rows="7"
      />
      <q-btn icon="create" class="full-width" @click="createArticle()">Create</q-btn>
    </div>

    <div v-if="!edit_mode">
      <q-card>
        <q-card-title>
          {{article.title}}
        </q-card-title>
        <q-card-separator />
        <q-card-main>
          {{article.content}}
        </q-card-main>
      </q-card>
    </div>
  </div>
</template>

<script>
import {
  LocalStorage,
  QInput,
  QBtn,
  QCard,
  QCardTitle,
  QCardSeparator,
  QCardMain
} from 'quasar'
import router from '../../../router'
export default {
  data () {
    return {
      article: {},
      edit_mode: false
    }
  },
  components: {
    QInput,
    QBtn,
    QCard,
    QCardTitle,
    QCardSeparator,
    QCardMain
  },
  mounted: function () {
    // LocalStorage.clear()
    // console.log(LocalStorage.get.item('articles'), this.$route.params.articleParam)
    let articles = LocalStorage.get.item('articles')
    if (typeof this.$route.params.articleParam !== 'undefined' && this.$route.params.articleParam === 'new') {
      this.edit_mode = true
    }
    else if (typeof this.$route.params.operate !== 'undefined' && this.$route.params.operate === 'edit') {
      this.article = articles[this.$route.params.articleParam]
      this.edit_mode = true
    }
    else {
      this.article = articles[this.$route.params.articleParam]
    }
  },
  methods: {
    createArticle: function () {
      let articles = LocalStorage.has('articles') ? LocalStorage.get.item('articles') : {}
      let count = Object.keys(articles).length
      ++count
      articles[count] = this.article
      LocalStorage.set('articles', articles)
      this.edit_mode = false
      router.push(`/article/${count}`)
    }
  }
}
</script>

<style>
</style>
