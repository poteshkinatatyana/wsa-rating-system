<template>
<div>
    <q-input v-model="editmode.title" label="Название" /> <br>
    <criteries-list-edit :criteriesdata="editmode.criteries" /> <br>
    <score-list-edit :scoredata="editmode.score"/> <br>
    <div >
      <q-btn outline color="indigo" @click="$emit('SaveModule')" class="q-mr-lg">Сохранить модуль</q-btn>

    <q-btn outline color="indigo" @click="$emit('CancelModule')">Закрыть</q-btn>
    </div>

</div>
</template>

<script>

import CriteriesListEdit from 'src/components/RatingPanel/CriteriesListEdit.vue'
import ScoreListEdit from 'src/components/RatingPanel/ScoreListEdit.vue'

export default {
  components:{CriteriesListEdit,ScoreListEdit},
  props:{
    editmode:Object
  }

}
</script>

<style>

</style>
