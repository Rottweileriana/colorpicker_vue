<template>
    <div class="container" id=id @click="getSC">
        <h4>Saved Colors</h4>
        <div v-for="(item, index) in items" :key="index" class="savedColor" :id="index">
            <li>{{item.colorName}} </li>
            <input type="radio" :value="index" name="colorSelect" @click="updateSC" v-model="selectColor"/>
        </div>
        <textarea type="text" id="Store" length="100" value='[{"colorName":"mainColor","colorCode":"#1e90ff"},{"colorName":"compColor","colorCode":"#e01010"},{"colorName":"accentColor","colorCode":"#EEFF00"},{"colorName":"colornr4","colorCode":"#FFF"}]'>
        </textarea>
    </div>
</template>

<script>
    let myJSON;
    let JsonParse;
   

export default {
 data () {
    return {
        items: [],
        selectColor: 0
    }
 },
    mounted(){
        myJSON = '[{"colorName":"mainColor","colorCode":"#1e90ff"},{"colorName":"compColor","colorCode":"#e01010"},{"colorName":"accentColor","colorCode":"#EEFF00"},{"colorName":"colornr4","colorCode":"#FFF"}]'
        let jsonData = document.getElementById("Store").value
        //console.log(jsonData);
        this.$emit('toParent', jsonData)
        JsonParse = JSON.parse(myJSON)
        this.items = JsonParse
    },
    
 methods: {
     updateSC(){
        this.$emit("updateSC", this.selectColor)
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
}

p{
    display: inline;
}

li{
    list-style: none;
    display: inline;
}

textarea{  
    width: 345px;
    height: 60px;
}
</style>