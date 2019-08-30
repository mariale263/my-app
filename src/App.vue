<template>
  <div id="app" class="container">
    
    <div class="hero is-dark is-gradient is-bold">
      <div class="hero-body">
        <h1 class="title">
          <span class="has-text-success">USUARIOS</span>
        </h1>
          <button class="button is-success is-rounded" v-on:click="fetch">Consultar</button>
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


