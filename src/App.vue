<template>
  <div id="app" class="container">
    
    <div class="hero is-dark is-gradient is-bold">
      <div class="hero-body">
        <h1 class="title">
          
          <span class="has-text-success">USUARIOS</span>
        </h1>
          <button class="button is-success is-rounded" v-on:click="fetch">Consultar</button>

          <!-- Agregando el loading-->
            <div align="center" *ngIf="productosService.cargando">
        <h2>Cargando</h2>

        <div class="loader loader--style1" title="0">
            <svg version="1.1" id="loader-1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px"
            width="40px" height="40px" viewBox="0 0 40 40" enable-background="new 0 0 40 40" xml:space="preserve">
            <path opacity="0.2" fill="#000" d="M20.201,5.169c-8.254,0-14.946,6.692-14.946,14.946c0,8.255,6.692,14.946,14.946,14.946
            s14.946-6.691,14.946-14.946C35.146,11.861,28.455,5.169,20.201,5.169z M20.201,31.749c-6.425,0-11.634-5.208-11.634-11.634
            c0-6.425,5.209-11.634,11.634-11.634c6.425,0,11.633,5.209,11.633,11.634C31.834,26.541,26.626,31.749,20.201,31.749z"/>
            <path fill="#000" d="M26.013,10.047l1.654-2.866c-2.198-1.272-4.743-2.012-7.466-2.012h0v3.312h0
            C22.32,8.481,24.301,9.057,26.013,10.047z">
            <animateTransform attributeType="xml"
                attributeName="transform"
                type="rotate"
                from="0 20 20"
                to="360 20 20"
                dur="0.5s"
                repeatCount="indefinite"/>
            </path>
            </svg>
        </div>

        <p>Espere por favor</p>
    </div>
            <!--Cerrando el loading -->

      </div>
    </div>

    <div class="container notification level is-mobile" v-for="usuario of usuarios" v-bind:key="usuario.id">
         
      <ul class="level-left ">
        <li><strong>Nº</strong></li>
        <li class="level-item has-text-centered">{{ usuario.id }}</li>
        <li class="level-item has-text-centered"><strong>Nombre:</strong></li>
        <li class="level-item has-text-centered">{{ usuario.name }}</li>
        <li class="level-item has-text-centered"><strong>Correo Electronico:</strong></li>
        <li class="level-item has-text-centered">{{ usuario.email }}</li>
      </ul>
     
    </div>
  </div>
</template>

<script>
//librerias
import axios from "axios";
import { constants } from 'crypto';

export default {
  name: 'app',
  data() {
    return {
      usuarios: [],
    };
  },

  methods: {
    fetch () {
      let result = axios
      .get("https://my-user-manager.herokuapp.com/users")
      .then((res) => {
        this.usuarios = res.data;  
        console.log(res.data)
      })
      .catch(err => console.error(err));
    }
  }
  };

</script>


