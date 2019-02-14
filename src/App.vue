<template>
  <div id="app">
    <h1>在线翻译</h1>
    <h5>简单/易用/便捷</h5>
   <translateform v-on:formSubmit="translateText"></translateform> 
   <translateoutput v-text="translatedText"></translateoutput>
  </div>
</template>

<script>
import Translateform from './components/Translateform'
import Translateoutput from './components/Translateoutput'

export default {
  name: 'App',
  components: {
    Translateform,
    Translateoutput
  },
  data:function(){
    return{
      translatedText:""
    }
  },
  methods:{
    translateText:function(text,language){
     // alert(text);
     this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20180719T030200Z.fc520f8c30fbfcea.404529ec767374301dd72cdb4dddd7192457ddcf&lang='+language+'&text='+text).then((response)=>{
            //console.log(response.body.text[0]);
            this.translatedText=response.body.text[0];
         })
     }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
