<template>
  <v-app>
    <v-main>
      <div ref="bg" id="bg">
        <div class="cad" :class="classe" ref="cad" v-show="cadastro">
            <Cadastro @login="close_cad" />
        </div>
        <Login v-if="!cadastro && login" @cadastro="open_cad"/>
      </div>
    </v-main>
  </v-app>
</template>

<script>
import Login from './components/Login';
import Cadastro from './components/Cadastro';

export default {
  name: 'App',
  data() {
    return {
      cadastro: false,
      login: true,
      classe: '',
    }
  },
  components: {
    Login, Cadastro
  },
  destroyed() {
      window.removeEventListener('resize', this.handleResize);
  },
  mounted() {
    window.addEventListener('resize', this.handleResize);
      this.handleResize();

  },
  methods: {
    open_cad(){
      console.log('teste')
      this.classe = 'anima'
      this.cadastro = true
      setTimeout(() => {
        this.login = true
      }, 500);
    },
    close_cad(){
      this.classe = 'anima2'
      setTimeout(() => {
      this.cadastro = false
        this.login = true
      }, 500);
    },
    handleResize() {
      if (this.cadastro == true && window.innerWidth < 700) {
        this.$refs['cad'].style.width = '100%'
      }else{
        this.$refs['cad'].style.width = '60%'
      }
    }
  },
  watch: {
    cadastro: {
      deep: true,
      handler(){
        if (this.cadastro == true && window.innerWidth < 700) {
          this.$refs['cad'].style.width = '100%'
        }else{
          this.$refs['cad'].style.width = '60%'
        }
      }
    }
  }
};
</script>

<style>
  #bg {
    height: 100vh;
    background: #C6FFDD;  /* fallback for old browsers */
    background: -webkit-linear-gradient(to right, #C4FCEF, #BED6FA, #FFC096);  /* Chrome 10-25, Safari 5.1-6 */
    background: linear-gradient(to right, #C4FCEF, #BED6FA, #FFC096); /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */

  }
  .cad {
    width: 60%; 
    float: left;
    background: white;
  }
  .anima{
    animation: scale-up-hor-left 0.4s cubic-bezier(0.390, 0.575, 0.565, 1.000) both;
  }
  .anima2{
    animation: scale-up-hor-right 0.4s cubic-bezier(0.390, 0.575, 0.565, 1.000) both;
  }
  @keyframes scale-up-hor-left {
    0% {
      -webkit-transform: scaleX(0.4);
              transform: scaleX(0.4);
      -webkit-transform-origin: 0% 0%;
              transform-origin: 0% 0%;
    }
    100% {
      -webkit-transform: scaleX(1);
              transform: scaleX(1);
      -webkit-transform-origin: 0% 0%;
              transform-origin: 0% 0%;
    }
  }
  @keyframes scale-up-hor-right {
    0% {
      -webkit-transform: scaleX(1);
              transform: scaleX(1);
      -webkit-transform-origin: 0% 0%;
              transform-origin: 0% 0%;
    }
    100% {
      -webkit-transform: scaleX(0);
              transform: scaleX(0);
      -webkit-transform-origin: 0% 0%;
              transform-origin: 0% 0%;
    }
  }
</style>
