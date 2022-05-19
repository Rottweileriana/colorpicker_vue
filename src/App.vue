<template>
  <div id="app" >
    <div class="containColorPicker">
    <!-- <Header  /> -->
    <ColorPicker @changeColor="liveUpdate"/>
    <ColorList v-on:updateSC="updateSC($event)" @click="clickHandler" @toParent="handler"/>
    <button @click="showColors">Show colors</button>
    </div>
    <div class="testerArea">
      <h1>Test</h1>
    </div>
  </div>

</template>

<script>
//import Header from '@/components/Header';
import ColorPicker from '@/components/ColorPicker';
import ColorList from '@/components/ColorList';
import './assets/style.css'

let rgb;
let black = "rgba(0, 0, 0, 1)";
let sc = 0;
let colorArray = [];
let r = document.querySelector(':root');
export default {
  name: 'app',
  components: {
    //Header,
    ColorPicker,
    ColorList,  
  },
  mounted() {
     
    
      
  },
  methods: {
    showColors(){  
      for (let i = 0; i < localStorage.length -1; i++) {
      let savedColors = document.getElementById(i);
      let element = localStorage[i];
      savedColors.style.background = element;
      //document.getElementById(i).style.background = colorArray[i].colorCode;
    }
    },
    handler(value){
      colorArray = JSON.parse(value)
      //console.log(colorArray);
    },
    updateSC(SC){
      sc = SC;  
    }, 
    liveUpdate(color){

      r.style.setProperty("--" + colorArray[sc].colorName, color)
      rgb = color;
    },
    clickHandler(e){
      localStorage.setItem(e.target.id, rgb)
      colorArray[e.target.id].colorCode = rgb;
      document.getElementById("Store").value = JSON.stringify(colorArray)
      document.getElementById(e.target.id).style.background = rgb;
      if(rgb == black){  
       document.getElementById(e.target.id).style.color = "#FFF"
      }
    }
  }
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

.containColorPicker{  
  display: inline-block;
  margin: 0;
  position: absolute;
  left: 10px;
}

.testerArea{  
  display: inline-block;
  width: 500px;
  height: 300px;
}
</style>