<template>
  <div id="app" >
    <Header  />
    <ColorPicker 
      @clicked="getColor" ref="colorPickerRef"/>
    <ColorList @click.shift.exact="clickHandler" @click.ctrl.exact="clickClick"/>
  </div>
</template>

<script>
import Header from '@/components/Header';
import ColorPicker from '@/components/ColorPicker';
import ColorList from '@/components/ColorList';
let rgb;
let savedColor1;
let savedColor2;
let savedColor3;
let savedColor4;
let savedColor5;
export default {
  name: 'app',
  components: {
    Header,
    ColorPicker,
    ColorList
  
  },
  mounted() {
      savedColor1 = localStorage.getItem(1)
      savedColor2 = localStorage.getItem(2)
      savedColor3 = localStorage.getItem(3)
      savedColor4 = localStorage.getItem(4)
      savedColor5 = localStorage.getItem(5)
      
      document.getElementById(1).style.background = savedColor1
      document.getElementById(2).style.background = savedColor2
      document.getElementById(3).style.background = savedColor3
      document.getElementById(4).style.background = savedColor4
      document.getElementById(5).style.background = savedColor5
    
  },
  methods: {
    clickClick(){
      this.$ColorPicker[0].myMethod()
      //this.$ColorPicker[0].changeColor(localStorage.getItem(document.getElementById(e.target.id)));
    },
    
    setColor(e){
      e.target.style.cssText = rgb
    },
   getColor(color){
     rgb = color;
     
   },
   clickHandler(e){
      savedColor1 = localStorage.getItem(1)
      savedColor2 = localStorage.getItem(2)
      savedColor3 = localStorage.getItem(3)
      savedColor4 = localStorage.getItem(4)
      savedColor5 = localStorage.getItem(5)
      //console.log(e.target.id);
      //console.log(rgb);
      
      localStorage.setItem(e.target.id, rgb)
     
      //console.log(localStorage.key(1));
      document.getElementById(e.target.id).style.background = rgb;
      //console.log(savedColor);
    },
   showSavedColors () {
       console.log("work");
      savedColor1 = localStorage.getItem(1)
      savedColor2 = localStorage.getItem(2)
      savedColor3 = localStorage.getItem(3)
      savedColor4 = localStorage.getItem(4)
      savedColor5 = localStorage.getItem(5)
      
      // document.getElementById(1).style.background = savedColor1
      // document.getElementById(2).style.background = savedColor2
      // document.getElementById(3).style.background = savedColor3
      // document.getElementById(4).style.background = savedColor4
      // document.getElementById(5).style.background = savedColor5
    }
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
