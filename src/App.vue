<template>
  <div id="app">
    <h1 id="title">在线翻译</h1>
    <h5 class="text-muted more">简单 / 快捷 / 方便</h5>
    <translateForm @formSubmit="translateText"></translateForm>
    <translateResult :contentText="translatedText"></translateResult>
  </div>
</template>

<script>
  import TranslateForm from './components/translateForm'
  import TranslateResult from './components/translateResult'
  export default {
    name: 'App',
    data(){
      return{
        translatedText: ''
      }
    },
    components:{
      TranslateForm,
      TranslateResult
    },
    methods:{
      // https://bootswatch.com/ 使用bootstrap样式
      // https://tech.yandex.com/ 注册获取key调用接口实习翻译
      translateText(text,language){
        console.log(text,language)
        this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20190426T031856Z.18b44da5843e4c2e.28fd16c9143bf47bb79868a1c9473163799754e4&lang='+language+'&text='+text)
          .then(resp => {
            console.log(resp)
            this.translatedText = resp.body.text[0]
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
  #title{
    margin-bottom: 20px;
  }
  .more{
    margin-bottom: 20px; 
  }
</style>
