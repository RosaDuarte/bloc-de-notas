<template>
  <div class="container mt-6">
      <div class="row">
        <div class="columns is-mobile">
          <div class="column is-8 is-offset-2">
            <h1 class="title is-2 is-mobile">Mis notas</h1>
          </div>
        </div>
        <div class="columns is-mobile">
          <div class="column is-8 is-offset-2">
            <input type="text" class="input is-medium" placeholder="Escribe tu nota" v-model="suNota" v-on:keyup.enter="agregarNota()">
          </div>
        </div>
        <div class="columns is-mobile">
          <div class="column is-8 is-offset-2">
            <h2 class="title is-3">¡Recordar!</h2>
          </div>
        </div>
        <div class="columns is-mobile">
          <div class="column column is-8 is-offset-2" v-if="notas.length===0">
            <h3>No tienes que recordar nada hoy</h3>
          </div>
          <div class="column column is-8 is-offset-2">
            <ul v-for="(nota, index) in notas" v-bind:key="index">
              <li class="box is-flex is-justify-content-space-between animate__animated animate__fadeInDown">
                <span v-on:click="actualizarNota(nota, index)" v-bind:class="[nota.estado===true? 'icon has-text-success':'', 'cursor']">
                  <i v-bind:class="[nota.estado === true ? 'far fa-check-circle': 'far fa-circle']"></i>
                  <!-- <i class="far fa-circle"></i>
                  <i class="far fa-check-circle"></i> -->
                </span>
                <h5>
                  {{nota.nombre}}
                </h5>
                <span class="cursor icon has-text-danger" v-on:click="eliminarNota(index)">
                  <i class="far fa-trash-alt"></i>
                </span>
              </li>
            </ul>
          </div>
        </div>
      </div>
  </div>
</template>

<script>

export default {
  data(){
    return {
      notas: [],
      suNota: ''
    }
  },
  mounted(){
    if(localStorage.getItem('notas')){
      try{
        this.notas = JSON.parse(localStorage.getItem('notas'));
      }catch(e){
        localStorage.removeItem('notas')
      }
    }
  },
  methods: {
    agregarNota(){
      
      const nota = {
        nombre: this.suNota,
        estado:false
      }

      this.notas.push(nota);
      this.suNota = '';
      this.guardarNota();
    },
    eliminarNota(index){
      this.notas.splice(index,1);
      this.guardarNota();
    },
    actualizarNota(nota, index){
      this.notas[index].estado = !nota.estado;
    },
    guardarNota(){
      const parsed = JSON.stringify(this.notas);
      localStorage.setItem('notas', parsed);
    }
  }
}
</script>

<style scoped>
  .title, h2{
    text-align: center;
    color: #542757;
    box-shadow: 0px 2px 0px #cd4d93;
  }  

  input, li{
    text-align: center;
    /* background-color: rgb(255, 138, 183, .4); */
    background-color: rgb(255, 250, 242, .7);
    color: #542757;
    font-size: 20px;
    border: 1px solid #cd4d93;
  }

  input::placeholder{
    color:#cd4d93;
  }

  input:focus{
    border: 1px solid #ff79bd;
  }

  input:active{
    box-shadow: 0px 0px 2px #ff79bd;
  }

  input:hover{
    box-shadow: 0px 0px 3px #ff79bd;
  }

  h3{
    text-align: center;
    color: #542757;
    font-size: 25px;
    background-color: rgb(255, 250, 242, .6);
    border-radius: 4px;
  }

  .cursor{
    cursor: pointer;
  }

  /* @media (min-width: 769px) and (max-width:1023px ) {
    .title{
      color: chartreuse;
    }

    input{
      width: 100%;
    }
  } */
</style>
  
