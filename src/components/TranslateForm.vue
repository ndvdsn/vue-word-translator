<template>
  <div class="row" id="translateForm">
    <div class="col-md-3">
    </div>
    <div class="col-md-6 col-md-offset-3">
    <form id="tranform" class="well" v-on:submit="formSubmit">
      <input class="form-control" type="text" v-model="textToTranslate" placeholder="Enter a word...">
      <select class="form-control" v-model="language">
        <option value="no">Norwegian</option>
        <option value="pt">Portuguese</option>
        <option value="fr">French</option>
        <option value="gd">Gaelic</option>
      </select>
      <div class="col text-center">
        <br>
      <input class="btn btn-primary" type="submit" value="Translate">
      </div>
    </form>
    </div>
  </div>
</template>
<script>
export default {
  name: 'translateForm',
  data() {
    return {
      textToTranslate: '',
      language: ''
    }
  },
  created() {
    this.language = 'no';
  },
  methods: {
    formSubmit(e) {
      this.$emit('formSubmit', this.textToTranslate, this.language);
      e.preventDefault();
    }
  }
}
</script>
<style>
  #transform {
    border-radius:10px;
    border: 1px #ccc solid;
  }
</style>
