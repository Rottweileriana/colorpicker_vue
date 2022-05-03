<template>
    <div class="container" id=id>
        <h4>Saved Colors</h4>
        <div class="savedColor" id=1></div>
        <div class="savedColor" id=2></div>
        <div class="savedColor" id=3></div>
        <div class="savedColor" id=4></div>
        <div class="savedColor" id=5></div>
    </div>
</template>

<script>
export default {
    components:{
      
    },
     data () {
    return {
      color: "string"
    }
  },
 methods:{  clickHandler:function(e){
      console.log(e.target.id);
    },
     getColor(color){
         console.log(color);
     }
 }
}
</script>

<style scoped>
.container{
    margin: auto 0;
    background: #eee;
    width: 218px;
}
h4{
    margin: auto 10px;
}
.savedColor{
    width: 200px;
    height: 30px;
    margin: 0 auto;
}
</style>