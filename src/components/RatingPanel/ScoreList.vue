<template>




 <q-input bottom-slots  v-model="newScore" label="Добавить оценку"   :dense="dense">
      <template v-slot:append>
          <q-btn round dense flat icon="add" @click="addNewScore" />
        </template>
  </q-input>



 <q-list bordered separator>
      <q-item clickable v-ripple v-for="(score, idx) in scoredata" :key="idx">
        <q-item-section> <p>Описание оценки критерия <b>{{idx}}</b> - {{score}}</p></q-item-section>
      </q-item>
      </q-list>


</template>

<script>
export default {
  data(){
    return{
      newScore: null,
    }
  },
  props:{
    scoredata: Array,
  },
  methods:{
    addNewScore(){
      if(!this.newScore){
       console.log('Заполните поле')
     }else{
        this.scoredata.push(this.newScore)
        this.newScore = null
     }
    }

  }

}
</script>

<style>

</style>
