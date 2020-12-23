<template>
    <v-layout align-center justify-center>
        <v-flex xs12 sm8 md6 lg5 x14>
            <v-card >
                <v-toolbar dark color="blue-grey darken-3">
                    <v-toolbar-title >
                        Inicio de Sesión
                    </v-toolbar-title>
                </v-toolbar>
                <v-card-text>
                    <v-text-field v-model="email" autofocus color="cyan darken-2" label="Email" required>
                    </v-text-field>
                    <v-text-field v-model="password" type="password" color="cyan darken-2" label="Password" required>
                    </v-text-field>
                </v-card-text>
                <v-card-actions class="px-3 pb-3 ">
                    <v-flex text-xs-right>
                        <v-btn @click="ingresar()" dark color="blue-grey darken-1" elevation="3" >Ingresar</v-btn>
                    </v-flex>
                </v-card-actions>
            </v-card>
        </v-flex>
        
    </v-layout>

</template>
<script>
import axios from 'axios';
import swal from 'sweetalert';

export default {
    data(){
        return{
            email:'',
            password:'',
            
        }
    },

    methods:{
        ingresar(){
            axios.post('usuario/login',{email: this.email, password: this.password})
            .then(respuesta =>{
                 console.log(respuesta.data);
                return respuesta.data;
            })
            .then(data =>{
                swal("¡Bienvenido!", "Login exitoso", "success");
                this.$store.dispatch("guardarToken",data.tokenReturn);
                this.$router.push({name: 'home'});
            })
            .catch(error =>{
                //console.log(eror);
                console.log(error.response.status);
                if (error.response.status==401){
                    swal("Error", "Credenciales incorrectas", "error")
                } 
                else if (error.response.status==404){
                    swal("Error", "El usuario no existe", "error")
                }
                else{
                    swal("Error", "Ocurrió un error en el servidor", "error");
                }
            });
        }
    }
    
}
</script>
