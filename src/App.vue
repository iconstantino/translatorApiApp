<template>
  <div id="app">
    <h1>Word Translator</h1>
    <h5>Written with Vue.js</h5>
    <TranslateForm v-on:formSubmit="translateText"></TranslateForm>
    <TranslateOutput v-text="translatedText"></TranslateOutput>
  </div>
</template>

<script>
import TranslateForm from './components/TranslateForm'
import TranslateOutput from './components/TranslateOutput'

export default {
  name: 'app',
  components: {
    TranslateForm,
    TranslateOutput
  },
  data:function(){
      return{
        translatedText: ''
      }
  },
  methods: {
    translateText:function(text, language){
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20170413T082930Z.49ee9d7151ef21d3.dc42044f22486fac476bc7906dc1839a1c57c2d9&lang='+ language +'&text='+ text)
      .then((response) => {
        console.log(response.body.text[0]);
        this.translatedText = response.body.text[0];
      });
    }
  }
}
</script>

<style>
#app {
}
</style>
