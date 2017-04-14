<template>
  <div class="text-center" id="app">
    <h1>Word Translator</h1>
    <h5>Written with <img id="vue-logo-inline" src="https://cdn.auth0.com/blog/vuejs/vue-logo.png"></h5>
    <br>
    <h3 class="text-uppercase">Translates from English to a language of your choosing</h3>
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
        this.translatedText = response.body.text[0];
      });
    }
  }
}
</script>

<style>
body {
  background-color: #f9f9eb; 
}

#vue-logo-inline{
  max-height: 20px;
}
</style>
