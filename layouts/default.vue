<template>
  <v-app>
    <v-app-bar
      :clipped-left="clipped"
      fixed
      app
      flat
    >
    <v-card-title class="text-center py-6"> My project blog
      <!-- <h1 class="font-weight-bold display-3 basil--text">My project blog</h1> -->
    </v-card-title>
    <!-- <v-toolbar-title class="text-center justify-center"> My project blog</v-toolbar-title> -->

    </v-app-bar>

    <v-content>
      <v-container>
        <nuxt />
      </v-container>
    </v-content>

    <v-footer
      :absolute="!fixed"
      app
      color="black"
    >
      <span class="white--text">footer</span>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data () {
    return {
      clipped: false,
      drawer: false,
      fixed: false,
      menu:['HOME','BLOG','ABOUT'],
      items: [
        {
          icon: 'mdi-apps',
          title: 'Welcome',
          to: '/'
        },
        {
          icon: 'mdi-chart-bubble',
          title: 'Inspire',
          to: '/inspire'
        }
      ],
      miniVariant: false,
      right: true,
      rightDrawer: false,
      title: 'Vuetify.js'
    }
  }
}
</script>
