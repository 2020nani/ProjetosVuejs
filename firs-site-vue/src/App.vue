<template>
  <div id="app">
   <Header />
   <Home />
   <Footer />
  </div>
</template>

<script>
import Header from './components/Header';
import Home from './page/Home';
import Footer from './components/Footer';

import './Styles/Global.css';

export default {
  name: 'App',
  components: {
    Header,
    Home,
    Footer
  }
}
</script>

