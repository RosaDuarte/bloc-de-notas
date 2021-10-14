<template>
  <div class="fondo">
    <Navbar/>  
    <Notas/> 
  </div>   
</template>

<script>
import Navbar from './components/Navbar.vue'
import Notas from './components/Notas.vue'

export default {
  name: 'App',
  components: {
    Navbar,
    Notas  
  }
}

</script>


<style>
  
  #app{
    font-family: Helvetica, sans-serif;  
  }
  body, html{
    width: 100%;
    background: url("./assets/fondo2.jpg") no-repeat center center fixed;
    /* height: 100vh; */

    height: 100%;
    background-repeat: no-repeat;
    background-size: 100% 100%;
  }

  body::-webkit-scrollbar{
    width: 10px;
  }
  body::-webkit-scrollbar-thumb{
    background: #ffc4e2;
    border-radius: 4px;
  }
  body::-webkit-scrollbar-thumb:hover{
    background: #ff8ab4;
    box-shadow: 0px 0px 2px #ffc4e2;
  }
  body::-webkit-scrollbar-thumb:active{
    background: #f1f2f3;
  }
  body::-webkit-scrollbar-track {
    background: #ebe1fd;
    border-radius: 10px;  
  }
  body::-webkit-scrollbar-track:hover, body::-webkit-scrollbar-track:active {
  background: #ffc4e2;
}


</style>
