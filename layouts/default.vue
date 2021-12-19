<template>
  <v-app>
    <v-navigation-drawer app
    v-model="drawer"
    :clipped= "$vuetify.breakpoint.lgAndUp"
    >
      <div>
        botones
      </div>

    </v-navigation-drawer>
    <v-app-bar app :clipped-left= "$vuetify.breakpoint.lgAndUp">

    <v-app-bar-nav-icon icon @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
    <v-toolbar-tittle v-text="title"></v-toolbar-tittle>
   </v-app-bar>



    <v-main>
      <nuxt/>
    </v-main>

  <v-footer padless>
    <v-row justify="center" no-gutters>
        <v-btn color="primary" small icon> <v-icon>mdi-facebook</v-icon></v-btn>
        <v-btn color="primary" small icon> <v-icon>mdi-linkedin</v-icon></v-btn>
        <v-btn color="primary" small icon> <v-icon>mdi-twitter</v-icon></v-btn>
        <v-btn color="primary" small icon> <v-icon>mdi-instagram</v-icon></v-btn>
    <v-col class="text-center primary--text" cols="12">
      &copy; {{new Date().getFullYear()}} - Las recetas de Yoly
    </v-col>

    </v-row>
  </v-footer>

  </v-app>


</template>

<script>
export default {
  name: 'DefaultLayout',
  data () {
    return {
      drawer: false,
      title: "Las recetas de Yoly"

    }
  }
}
</script>
