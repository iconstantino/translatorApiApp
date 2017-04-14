<template>
  <div class="row" id="translateForm">
    <div class="col-md-6 col-md-offset-3">
        <form id="transForm" class="well form-inline" v-on:submit="formSubmit">
            <input class="form-control" type="text" v-model="textToTranslate" placeholder="Enter a word or a phrase">
            <select class="form-control" v-model="language">
                <option value="es" >Spanish</option>
                <option value="fr" >French</option>
                <option value="it" >Italian</option>
                <option value="de" >German</option>
                <option value="ru" >Russian</option>
                <option value="zh" >Chinese</option>
                <option value="ko" >Korean</option>
                <option value="ar" >Arabic</option>
            </select>
            <br><br>
            <input class="btn btn-success" type="submit" value="Translate">
        </form>
    </div>
  </div>
</template>

<script>
export default {
  name: 'translateForm',
  data(){
      return {
          textToTranslate: '',
          language: ''
      }
  },
  created() {
    this.language = 'es';
  },
  methods: {
      formSubmit(e){
          this.$emit('formSubmit', this.textToTranslate, this.language);
          e.preventDefault();
      }
  }
}
</script>

<style>
#transForm {
    border-radius: 10px;
    border: 1px grey solid;
}
</style>
