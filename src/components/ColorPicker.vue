<template>
<div>
  <div class="container">
    <ColorPicker
      theme="light"
      :color="color"
      :sucker-hide="true"
      :sucker-canvas="suckerCanvas"
      :sucker-area="suckerArea"
      @changeColor="changeColor"
      @openSucker="openSucker"
      @click="getColor"
    />
  </div>
</div>
</template>

<script>
  import { ColorPicker } from 'vue-color-kit'
  import 'vue-color-kit/dist/vue-color-kit.css'
  
  export default {
    components: {
      ColorPicker,
    },
    data() {
      return {
        color: '#59c7f9',
        suckerCanvas: null,
        suckerArea: [],
        isSucking: false,
      }
    },
    props:{
      
    },
    methods: {
      myMethod(){
        console.log("mymethod");
      },
      changeColor(color) {
        const { r, g, b, a } = color.rgba
        this.color = `rgba(${r}, ${g}, ${b}, ${a})`
        this.$emit("changeColor", this.color)
      },
      openSucker(isOpen) {
        if (isOpen) {
          // ... canvas be created
          // this.suckerCanvas = canvas
          // this.suckerArea = [x1, y1, x2, y2]
        } else {
          // this.suckerCanvas && this.suckerCanvas.remove
        }
      },
      getColor(){
        this.$emit("clicked", this.color)
      }
    }
  }     
</script>