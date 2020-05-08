<template>
  <div id="app">
    <Uploader v-show="!submitted" @submitted="handleFormSubmit" />
    <Passes v-show="submitted" :passes="passes" :backgroundColor="backgroundColor" />
  </div>
</template>

<script>
import Passes from './components/Passes.vue'
import Uploader from './components/Uploader.vue'

export default {
  name: 'App',
  components: {
    Passes,
    Uploader
  },
  data: function() {
    return {
      submitted: false,
      passes: null,
      backgroundColor: ''
    }
  },
  methods: {
    handleFormSubmit(fields) {
      this.backgroundColor = fields.color;
      this.passes = fields.passes;
      this.submitted = true;
    }
  }
}
</script>

<style>
  html, body {
    height: 100%;
    margin: 0;
    padding: 0;
  }

  #app {
    display: flex;
    flex-direction: column;
    min-height: 100%;
  }
</style>
