<template>
  <!-- if you want automatic padding use "layout-padding" class -->
  <div class="layout-padding">
    <!-- your content -->
    <q-btn
      icon="settings_overscan"
      class="full-width"
      color="primary"
      :disable="!isMobile"
      @click="scan()"
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
  },
  methods: {
    scan: function () {
      cordova.plugins.barcodeScanner.scan(
        function (result) {
          alert('We got a barcode\n' +
            'Result: ' + result.text + '\n' +
            'Format: ' + result.format + '\n' +
            'Cancelled: ' + result.cancelled)
        },
        function (error) {
          alert('Scanning failed: ' + error)
        }
      )
    }
  }
}
</script>

<style>
</style>
