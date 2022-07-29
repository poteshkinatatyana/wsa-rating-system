<template>

 <q-splitter
      v-model="splitterModel"
      style="height: 100%"
    >
 <template v-slot:before>
        <q-tabs
          v-model="tab"
          vertical
          class="text-indigo"
        >
          <q-tab name="mails"  label="Название" />
          <q-tab name="alarms"  label="Критерий" />
          <q-tab name="movies"  label="Оценка" />
          <q-tab  label="Добавить модуль" outline color="dark" @click="$emit('AddNewModule')" />
        </q-tabs>
      </template>

      <template v-slot:after>
        <q-tab-panels
          v-model="tab"
          animated
          swipeable
          vertical
          transition-prev="jump-up"
          transition-next="jump-up"
        >
          <q-tab-panel name="mails">

            <q-input  v-model="module.title"  label="Название модуля" />
           </q-tab-panel>

          <q-tab-panel name="alarms">

             <criteries-list :criteriesdata="module.criteries" />
           </q-tab-panel>

          <q-tab-panel name="movies">

            <score-list :scoredata="module.score"/>
           </q-tab-panel>
        </q-tab-panels>
      </template>

    </q-splitter>

</template>


<script>
import { ref } from 'vue'
import CriteriesList from 'src/components/RatingPanel/CriteriesList.vue'
import ScoreList from 'src/components/RatingPanel/ScoreList.vue'
export default {
  data(){
    return{
      tab: ref('mails'),
      splitterModel: ref(20)
    }
  },
  components:{ CriteriesList,ScoreList},
  props:{
    module: Object
  }

}
</script>

<style>

</style>
