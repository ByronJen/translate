<template>
  <div id="app" class="container text-center">
    <h1>在线翻译</h1>
    <h5 class="text-muted">简单 / 易用 / 便捷</h5>
    <translateForm v-on:formSubmit="getFormSubmit"></translateForm>
    <translateOutput v-text="translatedText"></translateOutput>
  </div>
</template>

<script>
import TranslateForm from './components/TranslateForm'
import TranslateOutput from './components/TranslateOutput'

export default {
  name: 'App',
  data(){
    return{
      translatedText:""
    }
  },
  components: {
    TranslateForm,
    TranslateOutput
  },
  methods:{
    getFormSubmit(txt,lang){
      this.$http.get("https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20180715T070157Z.0e167c80f3f92a8c.6fae8560c1a8435f2d7c197258725d82f577d36e&lang="+lang+"&text="+txt)
      .then((response)=>{
        this.translatedText=response.body.text[0];
      })
    }
  }
}
</script>

<style>

</style>
