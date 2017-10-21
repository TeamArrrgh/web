<template>
  <v-app id="inspire" dark>
    <v-navigation-drawer
      clipped
      persistent
      v-model="drawer"
      enable-resize-watcher
      app
    >
      <v-list dense>
        <v-list-tile @click="">
          <v-list-tile-action>
            <v-icon>dashboard</v-icon>
          </v-list-tile-action>
          <v-list-tile-content>
            <v-list-tile-title>Dashboard</v-list-tile-title>
          </v-list-tile-content>
        </v-list-tile>
        <v-list-tile @click="">
          <v-list-tile-action>
            <v-icon>settings</v-icon>
          </v-list-tile-action>
          <v-list-tile-content>
            <v-list-tile-title>Settings</v-list-tile-title>
          </v-list-tile-content>
        </v-list-tile>
        <v-list-tile @click="">
          <v-list-tile-action>
            <v-icon>trending_up</v-icon>
          </v-list-tile-action>
          <v-list-tile-content>
            <v-list-tile-title>Most Popular</v-list-tile-title>
          </v-list-tile-content>
        </v-list-tile>
        <v-list-tile @click="">
          <v-list-tile-action>
            <v-icon>help</v-icon>
          </v-list-tile-action>
          <v-list-tile-content>
            <v-list-tile-title>Help</v-list-tile-title>
          </v-list-tile-content>
        </v-list-tile>
      </v-list>
    </v-navigation-drawer>
    <v-toolbar app fixed clipped-left>
      <v-toolbar-side-icon @click.stop="drawer = !drawer"></v-toolbar-side-icon>
      <v-toolbar-title>
        <img src="~/assets/images/logo.png" alt="" class="dashboard-logo">
      </v-toolbar-title>
    </v-toolbar>
    <main>
      <v-content>
        <v-container fluid fill-height>
          <v-layout justify-center align-center>
            <div class="flex xs6">
              <h4>adWord: Spokane</h4>
              <line-chart 
              :chart-data="datacollection"></line-chart>
            </div>
            <div class="flex xs6">
              <bar-chart 
            :chart-data="datacollection"></bar-chart>
            </div>
            
          </v-layout>
         
        </v-container>
      </v-content>
    </main>
    <v-footer app fixed>
      <span>&copy; Powered by Simplexity</span>
    </v-footer>
  </v-app>
</template>

<script>
  import Vue from 'vue'
  import Vuetify from 'vuetify'
  import('~/node_modules/vuetify/dist/vuetify.min.css')
  import LineChart from '~/components/LineChart.vue'
  import BarChart from '~/components/BarChart.vue'
  
 
  Vue.use(Vuetify)
  export default {
    components: {
      LineChart,
      BarChart
    },
    data () {

      return {
        drawer: true,
        datacollection: {
          labels: ['January', 'February', 'March', 'April', 'June', 'July', 'Agust', 'Septemeber', 'October', 'November', 'December'],
          datasets: [
            {
              label: 'Data One',
              borderColor: '#FC2525',
              pointBackgroundColor: 'white',
              borderWidth: 1,
              pointBorderColor: 'white',
              backgroundColor: this.gradient,
              data: [40, 39, 10, 40, 39, 80, 40]
            },
            {
              label: 'Data Two',
              borderColor: '#05CBE1',
              pointBackgroundColor: 'white',
              pointBorderColor: 'white',
              borderWidth: 1,
              backgroundColor: this.gradient2,
              data: [60, 55, 32, 10, 2, 12, 53]
            }
          ]
        }
      }
    },
    props: {
      source: String
    }
  }
</script>

<style>
  .dashboard-logo{
    line-height: 1;
    max-width: 200px;
  }
  .toolbar__title{
    line-height: 1;
  }

</style>