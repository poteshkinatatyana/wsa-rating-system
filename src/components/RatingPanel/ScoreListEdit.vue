<template>

<!-- <input type="number" v-model.trim="newScore">
<button @click="addnewScore">+</button>

<div v-for="(s, idx) in scoredata" :key="idx">
{{s}} - <button @click="Remove(idx)">-</button>
</div>
 -->



<q-input bottom-slots  v-model.trim="newScore" label="Добавить Оценку"  :dense="dense">
      <template v-slot:append>
         <q-btn outline color="indigo"  icon="add" @click="addnewScore" >Добавить</q-btn>
        </template>
      </q-input>

 <q-list dense bordered padding class="rounded-borders">
      <q-item clickable v-ripple v-for="(s, idx) in scoredata" :key="idx">
        <q-item-section>
          <p>Описание оценки критерия <b>{{idx}}</b> - {{s}} <q-btn round dense flat icon="delete" @click="Remove(idx)" /></p>

        </q-item-section>
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
       Remove(e){
      this.scoredata.splice(e, 1);
    },
     addnewScore(){
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
