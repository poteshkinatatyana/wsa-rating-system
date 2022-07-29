<template>

<div class="bg">
<div class="border">

      <index-page  v-if="!welcome" key="0" @WelcomeGo="WelcomeGo"/>
      <rating-panel v-else key="1" />

 </div>
</div>


</template>

<script>
import {  ref } from 'vue'
import IndexPage from 'src/pages/IndexPage.vue'
import RatingPanel from 'src/pages/RatingPanel.vue'


export default ({
  name: 'MainLayout',

  data(){
    return{
      welcome:null,
    }
  },
  methods:{
    WelcomeGo(weltrue){
      this.welcome = weltrue;
    }
  },
  components: {
  IndexPage, RatingPanel
  },


})
</script>

<style>

body {
  margin:0;
 font-family: 'Montserrat', sans-serif !important;
}

.bg {
   background: url('assets/banner.png') no-repeat center center fixed;
  -webkit-background-size: cover;
  -moz-background-size: cover;
  -o-background-size: cover;
  background-size: cover;
  position:fixed;
  top:0;
  left:0;
  right:0;
  bottom:0;
  margin: 0;
}

.border{
    position:fixed;
  top:0;
  left:0;
  right:0;
  bottom:0;
  margin: 20px;
  padding:20px;
   border-radius:.25em;
  box-shadow:0 0 .25em rgba(0,0,0,.25);
}
</style>
