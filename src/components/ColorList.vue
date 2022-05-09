<template>
    <div class="container" id=id @click="getSC">
        <h4>Saved Colors</h4>
        <div class="savedColor" id=1>
            <p>MainColor</p> 
            <input type="radio" name="cs" v-model="selectColor" value="1" @click="updateSC" />
        </div>
        <div class="savedColor" id=2>
            <p>CompColor</p>    
            <input type="radio" name="cs" v-model="selectColor" value="2" @click="updateSC" />
        </div>    
        <div class="savedColor" id=3>
            <p>AccentColor</p> 
            <input type="radio" name="cs" v-model="selectColor" value="3" @click="updateSC" />
        </div>
    </div>
</template>

<script>

export default {
    components:{
      
    },
     data () {
    return {
        selectColor: 1
    }
 },
 methods: {
     updateSC: function(){
         this.$emit("updateSC", this.selectColor)
         this.selectColor
         console.log(this.selectColor);
     },
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
    width: 218px;
    height: 30px;
    margin: 0 auto;
    /* background: aqua; */
}

p{
    display: inline;
}
</style>