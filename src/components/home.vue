<template>
<div>
        <div >
            <div >
                <v-carousel :show-arrows="false">
                    <v-carousel-item 
                    v-for="(item,i) in items"
                    :key="i"
                    :src="item.src"
                    reverse-transition="fade-transition"
                    transition="fade-transition"
                    ></v-carousel-item>
                </v-carousel>
            </div>
        </div>
        <div>
            <p></p>
        </div>
        <div class="container-fluid">
            <h2 class="row justify-content-center mb-5 font-weight-black">Nuestros Servicios</h2>
            <div class="row justify-content-center mb-5">
                <div v-for="item in categoria" :key="item.codigo" class="col mt-5">
                        <v-card
                            class="mx-auto"
                            max-width="400"
                        >
                            <v-img
                            class="white--text align-end"
                            height="400px"
                            :src="item.image"
                            >
                            
                            </v-img>
                            <v-card-title>{{item.nombre}}</v-card-title>
                            <v-card-text class="text--primary">
                            <div>{{item.descripcion}}</div>
                            </v-card-text>
                    
                        </v-card>
                    
                </div>
            </div>
        </div>
        <div></div>
        <div class="container-fluid">
            <h2 class="row justify-content-center mb-5 font-weight-black">Acerca de Nosotros</h2>
            <div class="row mb-5 justify-content-center">
                <div class="col justify-content-center" >
                        <div class="d-flex justify-content-center align-items-center">
                                <div class="p-3">
                                    <img src="https://d2qc4bb64nav1a.cloudfront.net/cdn/13/images/curso-online-coaching-y-mentoring_amp_primaria_1_1560502986.jpg" width="900" height="450" border="0" >
                                </div>
                                <div class="p-3">
                                <p>Desde nuestro nacimiento hace 1 década, nos hemos comprometido con la excelencia y la vanguardia organizacional, acompañando y transformando
                                a las mejores organizaciones en todo el mundo, teniendo presencia en Colombia y Sudamérica.<p>

                                <p> Nuestro equipo esta conformado por consultores de primer nivel, que integran su vasta experiencia en el campo de las organizaciones y su solida
                                y constante preparación para dar como resultado la mas exitosa combinación.</p> 

                                <p>Hemos generado ideas que cambian paradigmas y presenciado equipo que imaginan y crean, limites mentales que se desvanecen, canales de comunicación
                                que se fortalecen y liderazgos que se forjan con la voluntad de cada momento.</p> 

                                <p>Estos somos y esta es nuestra visión para tu organización.</p> 
                                </div>
                            </div>
                        </div>
                
            </div>
        </div>
        <div></div>
        <div class="container-fluid">
            <h2 class="row justify-content-center mb-5 font-weight-black">Nuestro Equipo</h2>
            <div class="row justify-content-center mb-5">
                <div v-for="miembro in team" :key="miembro.codigo" class="col mt-5">
                        <div class="card text-white bg-dark" >
                            <div class="d-flex justify-content-center p-2">
                                <img :src="miembro.image" width="200" height="200" border="0" class="pa-7 secondary rounded-circle d-inline-block">
                            </div>
                            <div class="card-body">
                                <h5 class="card-title text-center"> {{miembro.rol}}</h5>
                                <h5 class="card-title"> {{miembro.nombre}}</h5>
                                <p class="card-text">{{miembro.descripcion}}
                                </p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        <div></div>
          <div class="container-fluid">
            <h2 class="row justify-content-center mb-5 font-weight-black">Casos de exito</h2>
                <div clas="d-flex container-fluid flex-wrap">
                    <div class="row mt-md-5 mt-sm-5 mt-xs-5" >
                        <div class="col-lg-4 col-xs-8" v-for="url in casoexito" :key="url.codigo">
                            <div clas="container-fluid" >
                                <div class="d-flex justify-content-center align-items-center">
                                    <div class="p-3">
                                        <img :src="url.src" width="400" height="400" border="0" >
                                    </div>
                                    
                                </div>
                                
                            </div>
                        </div>
                    </div>
            </div>
    </div>
    </div>
</template>


<script>
import axios from 'axios';
export default {
     data() {
         return {
            datos: null,
            items: [
                {
                    src: 'https://i.imgur.com/IbmMxsi.jpg',
                },
                {
                    src: 'https://i.imgur.com/yqzghX4.jpg',
                },
                {
                    src: 'https://i.imgur.com/Aw8TfGM.jpg',
                },
                {
                    src: 'https://i.imgur.com/xFOKDos.jpg',
                },
             ],

             casoexito: [
                {
                    codigo: 1,
                    src: 'https://noravillegas.com/templates/yootheme/cache/06_CoachingNoraVillegas-9508c163.webp',
                },
                {
                    codigo: 2,
                    src: 'https://noravillegas.com/templates/yootheme/cache/15_CoachingNoraVillegas-708dfcb3.webp',
                },
                {
                    codigo: 3,
                    src: 'https://noravillegas.com/templates/yootheme/cache/05_CoachingNoraVillegas-7b0c2032.webp',
                },
                {
                    codigo: 4,
                    src: 'https://noravillegas.com/templates/yootheme/cache/SieteChakras_noel_640_NOraVillegas-e82aafe5.webp',
                },
                {
                    codigo: 5,
                    src: 'https://noravillegas.com/templates/yootheme/cache/07_CoachingNoraVillegas-cf0b61ac.webp',
                },
                {
                    codigo: 6,
                    src: 'https://noravillegas.com/templates/yootheme/cache/01_CoachingNoraVillegas-c873a54f.webp',
                }
              
             ],

              categoria: [{
                codigo: 1,
                nombre: 'Coaching Online',
                descripcion: 'Sesiones Online de Coaching.',
                image: 'https://www.guidocattaneo.com/wp-content/uploads/2019/02/coaching-online.jpeg'
            }, {
                codigo: 2,
                nombre: 'Coaching Presencial',
                descripcion: 'Sesiones Presenciales de Coaching.',
                image:'https://www.emprendiendohistorias.com/wp-content/uploads/2019/05/cursos-de-coaching-online.jpg'
            }, {
                codigo: 3,
                nombre: 'Gamificaciòn',
                descripcion: 'Sesiones interactivas para cambiar la rutina.',
                image:'https://i.imgur.com/N7NEaBq.jpg'
            }],
                  
            team: [  {
                    codigo: 1,
                    nombre: "Sebastián Cely",
                    descripcion: "Ingeniero Industrial. Hobbies: Videojuegos, escuchar música, programar, hacer deporte.",
                    rol: "Coach",
                    image: "https://drive.google.com/uc?export=download&id=1dTciNnYxilnMpnqQJMdaIKx_VUXjyh7C"
                },
                {
                    codigo: 2,
                    nombre: "Nicolás Cubillos",
                    descripcion: "Ingeniero Electrónico motivado por el aprendizaje de desarrollo de software, enfocado a solucionar y crear oportunidades para las empresas.",
                    rol: "Coach",
                    image: "https://images.unsplash.com/photo-1526374965328-7f61d4dc18c5?ixlib=rb-1.2.1&ixid=MXwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHw%3D&auto=format&fit=crop&w=1350&q=80"
                },
                {
                    codigo: 3,
                    nombre: "Camilo González",
                    descripcion: "Ingeniero de sistemas.                       Hobbies: Tecnología, fútbol y videojuegos.",
                    rol: "Coach",
                    image: "https://i.imgur.com/aesAWOn.jpeg"
                },
                {
                    codigo: 4,
                    nombre: "Daniel Saavedra",
                    descripcion: "Autodidacta primero, estudiante de economía después. Me apasiona la eficiencia y el uso de la tecnología para el impacto social y la solución de problemas.",
                    rol: "Coach",
                    image: "https://images.unsplash.com/photo-1588167056840-13caf6e4562a?ixid=MXwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHw%3D&ixlib=rb-1.2.1&auto=format&fit=crop&w=1001&q=80"
                }, 
                {
                    codigo: 5,
                    nombre: 'Patricia Arango',
                    descripcion: "administradora inmobiliaria",
                    rol: 'Coach',
                    image:"https://i.imgur.com/SaeoRxr.jpg"
                    }]
        };
    },
    mounted() {
     axios.get('articulo/list')
    .then(response => (this.datos = response.data));

    },
}
</script>