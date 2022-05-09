<template>
  <div id="app" >
    <Header  />
    <ColorPicker @clicked="getColor" @changeColor="liveUpdate" id="colorPicker"/>
    <ColorList v-on:updateSC="updateSC($event)" @click.ctrl.exact="clickHandler"/>
    <div>
      <h1>Test</h1>
    </div>
  </div>

</template>

<script>
import Header from '@/components/Header';
import ColorPicker from '@/components/ColorPicker';
import ColorList from '@/components/ColorList';
import './assets/style.css'
let rgb;
let sc
let savedColor1;
let savedColor2;
let savedColor3;
let r = document.querySelector(':root');
export default {
  name: 'app',
  components: {
    Header,
    ColorPicker,
    ColorList,  
  },
  mounted() {
      savedColor1 = localStorage.getItem(1)
      savedColor2 = localStorage.getItem(2)
      savedColor3 = localStorage.getItem(3)
      
      document.getElementById(1).style.background = savedColor1
      document.getElementById(2).style.background = savedColor2
      document.getElementById(3).style.background = savedColor3
  },
  methods: {
    updateSC: function(SC){
      console.log("value from updateSC in App "+SC);
      sc = SC;
    }, 
   getColor(color){
     rgb = color;     
   },
   clickHandler(e){
      savedColor1 = localStorage.getItem(1)
      savedColor2 = localStorage.getItem(2)
      savedColor3 = localStorage.getItem(3)      
      localStorage.setItem(e.target.id, rgb)
      document.getElementById(e.target.id).style.background = rgb;
    },
    liveUpdate(rgb){
      // let pressedKey = document.getElementById("colorPicker")
      // pressedKey.addEventListener("keydown", (e) =>{
        console.log('=============LIVE=======================');
        console.log(sc);
        console.log('====================================');
      if(sc == 1){r.style.setProperty("--mainColor", rgb)}
      if(sc == 2){r.style.setProperty("--compColor", rgb)}
      if(sc == 3){r.style.setProperty("--accentColor", rgb)}
      //})
      },
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #000000;
  margin-top: 60px;
}
</style> 
