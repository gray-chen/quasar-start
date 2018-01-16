<template>
  <!-- if you want automatic padding use "layout-padding" class -->
  <div class="layout-padding">
    <!-- your content -->
    <q-infinite-scroll :handler="loadMore">

      <q-list highlight>
        <q-item v-for="(article, index) in articles" :key="index" >
          <q-item-main @click="viewArticle(index)">
            <q-item-tile label>{{article.title}}</q-item-tile>
            <q-item-tile sublabel>{{article.title}}</q-item-tile>
          </q-item-main>
          <q-item-side right>
            <q-item-tile icon="mode_edit" color="green" @click="editArticle(index)" />
          </q-item-side>
          <q-item-separator />
        </q-item>
      </q-list>
      <!--
        slot="message" for DOM element to display (in this example
        a dots spinner) when loading additional content
      -->
      <q-spinner-ball
        slot="message"
        :size="5"
        color="primary"
      >
      </q-spinner-ball>
    </q-infinite-scroll>
    <q-fixed-position corner="bottom-right" :offset="[18, 18]">
      <q-btn round color="primary" @click="addArticle()" icon="note_add" />
    </q-fixed-position>
  </div>
</template>

<script>
import {
  QInfiniteScroll,
  LocalStorage,
  QSpinnerBall,
  QFixedPosition,
  QBtn,
  QList,
  QItem,
  QItemTile,
  QItemSide,
  QItemMain,
  QItemSeparator
} from 'quasar'
import router from '../../../router'
export default {
  data () {
    return {
      articles: LocalStorage.get.item('articles') || {}
    }
  },
  methods: {
    loadMore: function (index, done) {
      // index - called for nth time
      // done - Function to call when you made all necessary updates.
      //        DO NOT forget to call it otherwise your loading message
      //        will continue to be displayed
      // make some Ajax call then call done()
    },
    addArticle: function () {
      router.push('/article/new')
    },
    viewArticle: function (index) {
      router.push('/article/' + index)
    },
    editArticle: function (index) {
      router.push('/article/' + index + '/edit')
    }
  },
  components: {
    QInfiniteScroll,
    LocalStorage,
    QSpinnerBall,
    QFixedPosition,
    QBtn,
    QList,
    QItem,
    QItemTile,
    QItemSide,
    QItemMain,
    QItemSeparator
  },
  mouted: {
  }
}
</script>

<style>
</style>
