<template>      
      <div class="painel">
        <h2 class="painel-titulo" @dblclick="visivel = !visivel">{{titulo}}</h2>
        <transition name="painel-fade">
          <div class="painel-conteudo" v-show="visivel">
            <slot> </slot>
          </div>
        </transition>
      </div>
</template>

<script>
export default {
  data() {
      return {
          visivel: true
      }
  },

  props: ['titulo']
}
</script>

<style scoped>
  .painel {
    padding: 0 auto;
    border: solid 2px grey;
    display: inline-block;
    margin: 5px;
    box-shadow: 5px 5px 10px grey;
    width: 200px;
    height: 100%;
    vertical-align: top;
    text-align: center;
  }

  .painel .painel-titulo {
    text-align: center;
    border: solid 2px;
    background: lightblue;
    margin: 0 0 15px 0;
    padding: 10px;
    text-transform: uppercase;
  }

  * {
      box-shadow: 5px 5px 5px black;
  }
/*painel-fade-enter // antes do elemento ser incluido ou removido, estado atual
painel-fade-enter-active // quando o elemento esta sendo incluido
painel-fade-leave-active // quando o elemento esta sendo removido*/
.painel-fade-enter, .painel-fade-leave-active{
    opacity: 0;
}

.painel-fade-leave-active, .painel-fade-enter-active {
    transition: opacity .4s;;
}

</style>


