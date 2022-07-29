<template>

<div class="welcome-text">
    <h3>Система регионального <br> оценивание WSA</h3>
    <q-btn outline color="indigo" label="Начать"  size="25px" @click="$emit('WelcomeGo', true)"/>
</div>


</template>

<script>
export default {

}
</script>

<style scoped>
.welcome-text{
  text-align: center;
  position: absolute;
  top: 50%;
  left: 0;
  right: 0;
  bottom: 0;
  transform: translateY(-50%);
  min-height: 200px;
}
.welcome-text h3{
  line-height: 100px;
  font-size: 55px;
  text-transform: uppercase;
  font-weight: bold;
  background: rgb(131,58,180);
  background: linear-gradient(90deg, rgba(131,58,180,1) 0%, rgba(253,29,29,1) 50%, rgba(252,176,69,1) 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}
</style>
