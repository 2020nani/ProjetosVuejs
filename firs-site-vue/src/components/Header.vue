<template>
 <header>
     <nav class="container">
         <a href="/"><img src="https://raw.githubusercontent.com/william-costa/wdev-mock-site-resources/master/assets/images/wdev.svg"
          alt="Logo" id="logo"/></a>
         <img v-on:click="openMenu" id="menu-button"  alt="botao de menu"
         src="https://raw.githubusercontent.com/william-costa/wdev-mock-site-resources/master/assets/images/menu.svg"/>

         <div v-on:click="closedMenu" id="menu-overlay" v-if="menuActive"> </div>

         <div id="menu-items" :class="{active:menuActive}" >

             <a href="www.google.com.br"><img src="https://raw.githubusercontent.com/william-costa/wdev-mock-site-resources/master/assets/images/wdev.svg"
          alt="Logo" id="menu-logo"/></a>

             <ul>
                 <li><a href="/">Home</a></li>
                 <li><a href="/">Videos</a></li>
                 <li><a href="/">Sobre</a></li>
                 <li><a href="/">Contato</a></li>
             </ul>
         </div> 
        
     </nav>
 </header>
</template>

<script>


export default{
    name: 'Header',
    data() {
        return {
            menuActive: false
        }
    },
    methods: {
        openMenu: function(){
            this.menuActive = true;
        },
        closedMenu: function(){
            this.menuActive = false;
        }
    }
}

</script>

<style scoped >
  header {
     background-color: var(--color-background-nav);
     height: 10vh;
     width: 100%;
     display: flex;
     justify-content: center;
  }
  nav{
     display: flex;
     justify-content: space-between;
     align-items: center;
  }
  #logo{
      width: 150px;
  }
  #menu-logo{
      width: 110px;
      margin-top: 30px;
      margin-bottom: 10px;
  }
  #menu-button{
      width: 50px;
  }
  #menu-overlay{
      position:fixed;
      top: 0;
      left: 0;
      width: 40%;
      height: 100vh;
      background-color: black;
      opacity: 0.8;
  }
  #menu-items{
      position:fixed;
      top: 0;
      right: 0;
      width: 60%;
      height: 100vh;
      background-color: var(--color-background-nav);
      display: none;
      flex-direction: column;
      align-items: center;
      
  }

  #menu-items.active{
      display: flex;
  }

  ul{
      list-style: none;
      text-align: center;
  }

  ul li{
      margin: 20px 0;
  }

  ul li a{
      color: var(--color-text-light)
  }

  @media (min-width:700px) {
      #menu-button,
      #menu-logo,
      #menu-overlay{
          display: none;
      }
      #menu-items{
          display: flex;
          position: static;
          height: 60px;
          width: auto;
      }

      ul{
          display: flex;
          height: 60px;
          align-items: center;
          
      }
      ul li {
          margin: 0;
          margin-left: 20px;
      }
  }
</style>