<template>
  <!-- if you want automatic padding use "layout-padding" class -->
  <div class="layout-padding">
    <!-- your content -->
    <q-btn
      icon="settings_overscan"
      class="full-width"
      color="primary"
      :disable="!isMobile"
    >
      Scan a QRCode
    </q-btn>
  </div>
</template>

<script>
import {
  QBtn
} from 'quasar'
export default {
  data () {
    return {
      isMobile: !!this.$q.platform.is.mobile
    }
  },
  components: {
    QBtn
  }
}
</script>

<style>
</style>
