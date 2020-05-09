<template>
    <div id="uploader">
      <div class="input-wrapper">
        <label for="file">Choose A File:</label>
        <input id="file" type="file" @change="parseFile" />
      </div>
      <div class="input-wrapper">
        <label for="color">Background Color:</label>
        <chrome-picker v-model="color" />
      </div>
      <button type="submit" @click="submit">Submit</button>
    </div>
</template>

<script>
import Papa from 'papaparse';
import { Chrome } from 'vue-color';

export default {
  name: 'Uploader',
  data: function() {
    return {
      parsedData: null,
      color: '#fff'
    }
  },
  components: {
    'chrome-picker': Chrome,
  },
  methods: {
   parseFile(event) {
      let self = this;

      Papa.parse(event.target.files[0], {
        header: true,
        transformHeader: function(h) {
          return h.toLowerCase().replace(" ", "_")
        },
        complete: function(results) {
          self.parsedData = results.data;
        }
      });
   },
   submit() {
      this.$emit('submitted', {
        color: this.color.hex,
        passes: this.parsedData
      })
   }
  }
}
</script>

<style>
  #uploader {
    justify-content: center;
    align-self: center;
  }

  .input-wrapper {
    margin-bottom: 10px;
  }

  label {
    display: block;
    margin-bottom: 10px;
  }
</style>