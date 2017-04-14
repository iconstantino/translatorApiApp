<template>
  <div id="Translate Form">
    <Form v-on:submit="formSubmit">
        <input type="text" v-model="textToTranslate" placeholder="Enter a word">
        <select v-model="language">
            <option value="es" >Spanish</option>
            <option value="ru" >Russian</option>
            <option value="fr" >French</option>
            <option value="de" >German</option>
            <option value="da" >Danish</option>
            <option value="ch" >Chinese</option>
        </select>
        <input type="submit" value="Translate">
    </form>
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
</style>
