<template>
<div id="passes">
  <div v-for="pass in passes" class="pass" :style="'background-color: ' + backgroundColor" :key="pass.family">
    <div class="row top">
      <img src="@/assets/logo.png" />
      <span class="ccca">CCCA</span>
    </div>
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
</template>

<script>

export default {
  name: 'Passes',
  props: {
    passes: Array,
    backgroundColor: String
  }
}
</script>

<style>
@media print {
  html, body {
    height: auto;
    font-size: 12pt;
  }

  @page { 
    margin: 0;
    size: 8.5in 11in;
  }

  .pass {
    height: 264px;
    page-break-inside:avoid;
  }
}

#passes {
  width: 100%;
  margin: 0;
  display: grid;
  grid-template-columns: auto auto;
  flex-flow: row wrap;
}

.pass {
  flex-direction: row;
  position: relative;
  
}

.pass .row {
  display: flex;
  width: 100%;
}

.pass span {
  font-family: Helvetica, sans-serif;
  margin: 0;
  z-index: 2;
  font-size: 2em;
  text-align: center;
}

.pass .top img {
  width: 30%;
  margin-right: auto;
}

.pass .top span {
  margin: 20pt 20pt 0 auto;
} 

.pass .middle {
  flex-direction: column;
  margin-top: -5%;
}

.pass .middle span + span {
  margin-top: .2em;
}

.pass .bottom {
  margin-top: 5%;
  display: flex;
  align-items: center;
}

.pass .bottom span {
  margin: 0 auto 20pt 20pt;
}

.pass .bottom span + span {
  margin: 0 20pt 20pt auto;
}

.pass .org {
  font-size: 1.5em;
}
</style>
