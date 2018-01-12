<template>
  <q-layout
    ref="layout"
    view="lhh Lpr fFf"
    :left-class="{'bg-grey-2': true}"
  >
    <q-toolbar slot="header" class="">
      <!--<q-btn
        flat
        @click="$refs.layout.toggleLeft()"
      >
        <q-icon name="menu" />
      </q-btn>-->

      <q-toolbar-title>
        Quasar App
        <div slot="subtitle">Running on Quasar v{{$q.version}}</div>
      </q-toolbar-title>
    </q-toolbar>
<!--

    <div slot="left">
      &lt;!&ndash;
        Use <q-side-link> component
        instead of <q-item> for
        internal vue-router navigationscan
      &ndash;&gt;

      <q-list no-border link inset-delimiter>
        <q-list-header>Essential Links</q-list-header>
        <q-item @click="launch('http://quasar-framework.org')">
          <q-item-side icon="school" />
          <q-item-main label="Docs" sublabel="quasar-framework.org" />
        </q-item>
        <q-item @click="launch('http://forum.quasar-framework.org')">
          <q-item-side icon="record_voice_over" />
          <q-item-main label="Forum" sublabel="forum.quasar-framework.org" />
        </q-item>
        <q-item @click="launch('https://gitter.im/quasarframework/Lobby')">
          <q-item-side icon="chat" />
          <q-item-main label="Gitter Channel" sublabel="Quasar Lobby" />
        </q-item>
        <q-item @click="launch('https://twitter.com/quasarframework')">
          <q-item-side icon="rss feed" />
          <q-item-main label="Twitter" sublabel="@quasarframework" />
        </q-item>
      </q-list>
    </div>
-->

      <router-view />

    <q-tabs slot="navigation" align="justify">
      <q-route-tab
        icon="home"
        to="/"
        exact
        slot="title"
        label="Home"
        class="relative-position"
        v-ripple
      />
      <q-route-tab
        icon="settings_overscan"
        to="/scan"
        exact
        slot="title"
        label="Scan"
        class="relative-position"
        v-ripple
      />
    </q-tabs>

  </q-layout>
</template>

<script>
import {
  QLayout,
  QToolbar,
  QToolbarTitle,
  QBtn,
  QIcon,
  QList,
  QListHeader,
  QItem,
  QItemSide,
  QItemMain,
  QTabs,
  QRouteTab,
  Ripple
} from 'quasar'
export default {
  data () {
    return {}
  },
  components: {
    QLayout,
    QToolbar,
    QToolbarTitle,
    QBtn,
    QIcon,
    QList,
    QListHeader,
    QItem,
    QItemSide,
    QItemMain,
    QTabs,
    QRouteTab
  },
  directives: {
    Ripple
  }
}
</script>

<style>
</style>
