<template>
  <div class="text-center" id="app">
    <h1>Word Translator</h1>
    <h5>Powered by Vue.js</h5>
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
  data: function() {
    return {
      translatedText: ''
    }
  },
  methods: {
    translateText: function(text, language) {
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20200418T175249Z.7e1585b68432e002.50d024e2e9213016d69b1eff1bf495b56c73c960&lang='+language+'&text='+text)
      .then((response)=> {
        this.translatedText = response.body.text[0];
      });
    }
  }
}
</script>
<style>
body {
  background: #fefefe;
}
</style>
