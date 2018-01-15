<template>
  <!-- if you want automatic padding use "layout-padding" class -->
  <div class="layout-padding">
    <!-- your content -->
    <q-infinite-scroll :handler="loadMore">
      <!-- Content, in this case some <p> tags -->
      <p v-for="article in articles" class="caption">
        Lorem ipsum dolor sit amet...
      </p>
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
  </div>
</template>

<script>
import {
  QInfiniteScroll,
  LocalStorage,
  QSpinnerBall
} from 'quasar'
export default {
  data () {
    return {
      articles: LocalStorage.get.item('articles') || []
    }
  },
  methods: {
    loadMore: function (index, done) {
      // index - called for nth time
      // done - Function to call when you made all necessary updates.
      //        DO NOT forget to call it otherwise your loading message
      //        will continue to be displayed
      // make some Ajax call then call done()
    }
  },
  components: {
    QInfiniteScroll,
    LocalStorage,
    QSpinnerBall
  },
  mouted: {
  }
}
</script>

<style>
</style>
