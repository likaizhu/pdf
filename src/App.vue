<template>
  <!-- <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
  </div> -->
  <div id="app">
    <div id="demo"></div>
    <div class="nav">
      <div class="left">向左</div>
      <div class="rigth">向右</div>
    </div>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import Pdfh5 from 'pdfh5';
import axios from 'axios';
import "pdfh5/css/pdfh5.css";
export default {
  name: 'App',
  components: {
    // HelloWorld
  },
  data () {
    return {
      pdfh5: null
    }
  },
  mounted () {
    axios
      .get('https://www.gjtool.cn/pdfh5/git.pdf', {
        responseType: 'arraybuffer'
      })
      .then(res => {
        this.pdfh5 = new Pdfh5('#demo', {
          data: res.data,
          scrollEnable: false,
        });
      });
  },
  methods: {

  }
}
</script>

<style>
html{
  width:100%;
  height: 100%;
}
body{
  width:100%;
  height: 100%;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  /* margin-top: 60px; */
  width: 100%;
  height: 100%;
}
.nav{
  position: absolute;
    left: 0;
    height: 2em;
    background: red;
    top: 50%;
    bottom: 50%;
    width: 100%;
    display: flex;
    justify-content: space-between;
}
</style>
