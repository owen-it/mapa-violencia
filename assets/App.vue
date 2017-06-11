<template>
  <v-app light>
    <v-navigation-drawer
      light
      persistent
      :mini-variant="miniVariant"
      :clipped="clipped"
      v-model="drawer"
    >
      <v-list class="pa-0">
        <v-list-item>
          <v-list-tile avatar tag="div">
            <v-list-tile-avatar>
              <img src="~assets/images/pegman.png" />
            </v-list-tile-avatar>
            <v-list-tile-content>
              <v-list-tile-title>Menu</v-list-tile-title>
            </v-list-tile-content>
          </v-list-tile>
        </v-list-item>
      </v-list>
      <v-list>
      <v-divider></v-divider>
        <v-list-item v-for="(item, i) in items" :key="i">
          <v-list-tile router :to="item.to">
            <v-list-tile-action>
              <v-icon>{{ item.icon }}</v-icon>
            </v-list-tile-action>
            <v-list-tile-content>
              <v-list-tile-title v-text="item.title"></v-list-tile-title>
            </v-list-tile-content>
          </v-list-tile>
        </v-list-item>
      </v-list>


    </v-navigation-drawer>
    
    
    <v-toolbar class="info" light fixed>
      <v-toolbar-side-icon light @click.native.stop="drawer = !drawer"></v-toolbar-side-icon>
      <v-toolbar-title v-text="title"></v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn icon light @click.native.stop="rightDrawer = !rightDrawer">
        <v-icon>menu</v-icon>
      </v-btn>
    </v-toolbar>


    <main>
      <v-container fluid>
        <v-slide-y-transition mode="out-in">
          <router-view></router-view>
        </v-slide-y-transition>
      </v-container>
    </main>


    <v-navigation-drawer
      light
      temporary
      :right="right"
      v-model="rightDrawer"
    >
      <v-list light>
        <v-list-item>
          <v-list-tile @click.native="right = !right">
            <v-list-tile-action>
              <v-icon>compare_arrows</v-icon>
            </v-list-tile-action>
            <v-list-tile-title>Alterar Posição</v-list-tile-title>
          </v-list-tile>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    
    <v-footer :fixed="fixed">
      <span>Owen It &copy; 2017</span>
    </v-footer>
  </v-app>
</template>

<script>
  import Meta from 'mixins/meta'

  export default {
    mixins: [
      Meta
    ],

    data () {
      return {
        clipped: false,
        drawer: true,
        fixed: false,
        items: [
          { icon: 'bubble_chart', title: 'Mapa da Violência', to: '/' }
        ],
        miniVariant: false,
        right: true,
        mini: false,
        rightDrawer: false,
        title: 'Mapa de Violência'
      }
    }
  }
</script>

<style lang="stylus">
  @import './stylus/main'
</style>