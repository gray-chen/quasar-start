<template>
  <!-- if you want automatic padding use "layout-padding" class -->
  <div class="layout-padding">
    <!-- your content -->
    <div v-if="edit_mode">
      <q-input v-model="article.title" float-label="Title" placeholder="Title" />
    </div>

    <q-input
      v-model="article.content"
      type="textarea"
      float-label="Textarea"
      :max-height="100"
      :min-rows="7"
    />
    <q-btn icon="create" class="full-width" @click="createArticle()">Create</q-btn>
    <div v-if="!edit_mode">
      222
    </div>
  </div>
</template>

<script>
import {
  LocalStorage,
  QInput,
  QBtn
} from 'quasar'
export default {
  data () {
    return {
      article: LocalStorage.has('articles') ? LocalStorage.get.item('articles').this.$route.params.articleParam ? LocalStorage.get.item('articles').this.$route.params.articleParam : {} : {},
      edit_mode: false
    }
  },
  components: {
    QInput,
    QBtn
  },
  mounted: function () {
    // LocalStorage.clear()
    console.log(LocalStorage.get.item('articles'))
    if (this.$route.params.articleParam === 'new') {
      this.edit_mode = true
    }
  },
  methods: {
    createArticle: function () {
      let count = LocalStorage.get.length('articles')
      count++
      let articles = LocalStorage.has('articles') ? LocalStorage.get.item('articles') : {}
      articles[count] = this.article
      LocalStorage.set('articles', articles)
      console.log(count)
    }
  }
}
</script>

<style>
</style>
