<template>
<div>
  <div v-if="estado">
     <nav class="navbar navbar-expand-lg sticky-top navbar-dark bg-dark ">
        <a class="navbar-brand " href="# ">
            <img src="https://www.flaticon.com/svg/static/icons/svg/3534/3534097.svg" width="30 " height="30
    " class="d-inline-block align-top " alt=" " loading="lazy "> SPRINT 5
        </a>
        <div class="collapse navbar-collapse justify-content-end " id="navbarNav ">
            <ul class="navbar-nav ">
                <li class="nav-item active ">
                    <a class="nav-link " v-on:click="ingresar" href="# ">Sistema <span class="sr-only ">(current)</span></a>
                </li>
            </ul>
        </div>
    </nav>
    
    <div>
      <home/>
    </div>
    <footer>

         <v-footer
          dark
          padless
        >
          <v-card
            class="flex"
            flat
            tile
          >
            <v-card-title class="row justify-content-center mb-5">
              <strong class="subheading">Get connected with us on social networks!</strong>
                <div class="d-flex justify-space-around mb-6">             
                  <a href="https://es-la.facebook.com/" target="_blank"><img src="https://www.flaticon.es/premium-icon/icons/svg/2504/2504903.svg" width="24" height="24"></a>
                  <a href="https://twitter.com/home" target="_blank"><img src="https://www.flaticon.es/svg/static/icons/svg/145/145812.svg" width="24" height="24"></a>
                  <a href="https://github.com/dsaavedr/semana-5-45" target="_blank"><img src="https://www.flaticon.es/svg/static/icons/svg/270/270798.svg" width="24" height="24"></a>
                  <a href="https://www.youtube.com/watch?v=NRhcvlcFmAg" target="_blank"><img src="https://www.flaticon.es/premium-icon/icons/svg/2504/2504965.svg" width="24" height="24"></a>
                </div> 
              
            </v-card-title>

            <v-card-text class="py-2 white--text text-center">
              {{ new Date().getFullYear() }} — <strong>TeamCoach</strong>
            </v-card-text>
          </v-card>
        </v-footer>

    </footer>
  </div>
  <div v-else>
  <v-app id="app">
    <v-navigation-drawer
      v-model="drawer"
      :clipped="$vuetify.breakpoint.lgAndUp"
      app
    >
      <v-list dense>
        <template>
          <v-list-item @click="home">
            <v-list-item-action>
              <v-icon>home</v-icon>
            </v-list-item-action>
            <v-list-item-title>
              Inicio
            </v-list-item-title>
          </v-list-item>
        </template>
        <template v-if="logueado">
          <v-list-group>
            <v-list-item slot="activator">
              <v-list-item-content>
                <v-list-item-title>
                  Almacén
                </v-list-item-title>
              </v-list-item-content>
            </v-list-item>
            <v-list-item :to="{name: 'categoria'}">
              <v-list-item-action>
                <v-icon>table_chart</v-icon>
              </v-list-item-action>
              <v-list-item-content>
                <v-list-item-title>
                  Categorías
                </v-list-item-title>
              </v-list-item-content>
            </v-list-item>
            <v-list-item :to="{name: 'articulo'}">
              <v-list-item-action>
                <v-icon>table_chart</v-icon>
              </v-list-item-action>
              <v-list-item-content>
                <v-list-item-title>
                  Artículos
                </v-list-item-title>
              </v-list-item-content>
            </v-list-item>
          </v-list-group>
          <v-list-group>
            <v-list-item slot="activator">
              <v-list-item-content>
                <v-list-item-title>
                  Accesos
                </v-list-item-title>
              </v-list-item-content>
            </v-list-item>
            <v-list-item :to="{name: 'usuario'}">
              <v-list-item-action>
                <v-icon>table_chart</v-icon>
              </v-list-item-action>
              <v-list-item-content>
                <v-list-item-title>
                  Usuarios
                </v-list-item-title>
              </v-list-item-content>
            </v-list-item>
          </v-list-group>
        </template> 
      </v-list>
    </v-navigation-drawer>

    <v-app-bar
      :clipped-left="$vuetify.breakpoint.lgAndUp"
      app
      color="silver darken-3"
      dark
    >
      <v-toolbar-title
        style="width: 300px"
        class="ml-0 pl-3"
      >
        <v-app-bar-nav-icon @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
        <span class="hidden-sm-and-down">Sistema</span>
      </v-toolbar-title>      
      <v-spacer></v-spacer>
      <v-btn @click="salir()" icon v-if="logueado">
        <v-icon>logout</v-icon> Salir
      </v-btn>
      <v-btn :to="{name: 'login'}" icon v-else>
        <v-icon>apps</v-icon> Login
      </v-btn>
    </v-app-bar>
    <v-content>
      <v-container
        fluid
        fill-height
      >
        <v-slide-y-transition mode="out-in">
          <router-view/>
        </v-slide-y-transition>
      </v-container>
    </v-content>
    <v-footer height="auto">
      <v-layout justify-center>
        <v-flex text-xs-center>
          <v-card flat tile color="primary" class="white--text">
            <v-card-text class="white--text pt-0">
              Proyecto final &copy;2020
            </v-card-text>
          </v-card>
        </v-flex>
      </v-layout>
    </v-footer>
  </v-app>
  </div>
  </div>
</template>

<script>
import home from './components/home.vue'
export default {
  components: { home },
  name: 'App',

    data () {
      return {
      drawer: false,
      estado:1,
      }
    },

  computed:{
    logueado(){
      return this.$store.state.usuario;
    },
  },
  created(){
    this.$store.dispatch("autoLogin");
  },
  methods:{
    salir(){
      this.$store.dispatch("salir");
      this.estado=1
    },

    ingresar(){
      this.estado=0
    },

    home(){
      this.estado=1

    }
  }
};
</script>
