<template>
<div class="corpo">

  <meu-menu :rotas="routes" />

  <transition name="pagina-fade">
    <router-view />
  </transition>
</div>
</template>

<script>

import { routes } from './routes';
import Menu from './components/shared/menu/menu.vue'
export default {
  components: {
      'meu-menu': Menu
    },
  
  data(){
    
    return {
      routes
    }
  }

}

 
</script>

<style>
 .corpo{
   font-family: Arial, Helvetica, sans-serif;
   width: 96%;
   margin: 0 auto;
 }

 .pagina-fade-enter, .pagina-fade-leave-active{
    opacity: 0;
}

.pagina-fade-leave-active, .pagina-fade-enter-active {
    transition: opacity .4s;;
}
 
</style>
