<template>
<div id="passes">
  <div class="page" v-for="(page, index) in getPages(passes)" :key="index">
    <div v-for="pass in page" class="pass" :style="'background-color: ' + backgroundColor" :key="pass.family">
      <img id="logo" src="@/assets/logo.png" />
      <span id="ccca">CCCA</span>
      <div class="row middle">
        <span>{{pass.name}}</span>
        <span>{{pass.street_number}} {{pass.street}}</span>
      </div>
      <div class="row bottom">
        <span class="org">carlisle commonwealth</span>
        <span>2020</span>
      </div>
    </div>
  </div>
</div>
</template>

<script>

export default {
  name: 'Passes',
  props: {
    passes: Array,
    backgroundColor: String
  },
  methods: {
    getPages: function() {
      var pages = [];
      
      if(!this.passes) {
        return pages;
      }

      for (var i=0; i<this.passes.length; i+=10) {
        pages.push(this.passes.slice(i, i+10));
      }
      return pages;
    }
  }
}
</script>

<style>
#passes {
  width: 100%;
  height: 100%;
}

.page {
  width: 21.59cm;
  height: 27.94cm;
  margin: 0 auto;
  display: grid;
  grid-template-columns: auto auto;
}

.pass {
  width: 7.5cm;
  height: 4.5cm;
  margin: 0 auto;
  position: relative;
  align-self: center;
  display: flex;
}

.pass #logo {
  position: absolute;
  top: 0;
  left: 0;
  width: 1.75cm;
}

.pass #ccca {
  position: absolute;
  top: 0.25cm;
  right: 0.25cm;
  font-size: 0.65cm;
} 

.pass .row {
  display: flex;
  width: 100%;
}

.pass span {
  font-family: Helvetica, sans-serif;
  font-weight: bold;
  margin: 0;
  z-index: 2;
  font-size: 0.5cm;
  text-align: center;
}

.pass .middle {
  flex-direction: column;
  align-self: center;
}

.pass .middle span + span {
  margin-top: .2em;
}

.pass .bottom {
  position: absolute;
  bottom: 0;
  display: flex;
  align-items: center;
}

.pass .bottom span {
  margin: 0 auto 0.25cm auto;
  font-size: 0.4cm;
}

.pass .bottom span + span {
  font-size: 0.75cm;
  font-weight: bold;
  margin: 0 0.25cm 0.25cm 0;
}
</style>
