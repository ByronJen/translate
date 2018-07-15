<template>
  <div class="row" id="translateForm">
    <div class="col-md-8 offset-2">
        <form id="transForm" class="form-inline" v-on:submit="formSubmit">
            <input class="form-control" type="text" placeholder="Enter Content" v-model="textToTranslate">
            <select class="form-control" v-model="language">
                <option value="en">English</option>
                <option value="ru">Russian</option>
                <option value="ko">Korean</option>
                <option value="ja">Janpenese</option>
            </select>
            <input class="btn btn-primary" type="submit" value="Translate">
        </form>
    </div>
  </div>
</template>

<script>

export default {
  name: 'translateForm',
  data(){
      return {
          textToTranslate:"",
          language:""
      }

  },
  methods:{
      formSubmit(e){
        //   alert(this.textToTranslate);
        this.$emit('formSubmit',this.textToTranslate,this.language);
          e.preventDefault();//取消默认事件
      }
  },
  created() {
      this.language='en'
  },
}
</script>

<style>
#transForm{
    border:1px solid #ccc;
    border-radius:10px;
    padding:30px;
}
</style>
