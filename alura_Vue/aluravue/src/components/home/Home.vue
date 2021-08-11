<template>
<div>
   <h1 class="centralizado">{{ titulo }}</h1>
   <input type="search" class="filtro" @input="filtro = $event.target.value" placeholder="Filtre por parte do titulo">

  <ul class="lista-fotos"> 
    <li class="lista-fotos-itens" v-for="foto of fotosComFiltro">
      
        <Painel :titulo="foto.titulo">
          <Img  :url="foto.url" :titulo="foto.titulo" />
          <Botao 
             tipo="button" 
             rotulo="Remover" 
             @botaoAtivado="remover(foto)"
             :confirmacao="false"
             estilo="perigo" />
        </Painel>
      
    </li>
  </ul>
</div>
</template>

<script>
import Painel from '../shared/painel/Painel.vue';
import imagemResponsiva from '../shared/imagem-responsiva/imagemResponsiva.vue';
import botao from '../shared/botao/Botao.vue';
export default {
  components: {
    'Painel' : Painel,
    'Img' : imagemResponsiva,
    'Botao' : botao
  },
  data() {
    return {
      titulo: "Alura Pic",
      fotos:[],
      filtro: ''
      
    }
  },

  computed: {
    fotosComFiltro(){
        if(this.filtro) {
        let exp = new RegExp(this.filtro.trim(), 'i');
         return this.fotos.filter(foto => exp.test(foto.titulo));
        }else{
          return this.fotos
        }
    }
  },

  methods: {
     remover(foto) {
         
           alert('remover a foto: ' + foto.titulo);
               
     }
  },

  created() {
    this.$http.get('http://localhost:3000/v1/fotos')
       .then(res => res.json())
       .then(fotos => this.fotos = fotos, err => console.log(err));

    
  }
}
</script>

<style>
 
 .centralizado{
   text-align: center;
 }
 .lista-fotos{
   list-style: none;
 }
 .lista-fotos-itens{
   display: inline-block;
 }
 
 .filtro{
   display: block;
   width: 100%;
 }
  
</style>
