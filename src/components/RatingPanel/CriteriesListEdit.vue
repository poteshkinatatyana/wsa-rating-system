<template>

 <q-input bottom-slots  v-model="newCriteria" label="Добавить критерий"  :dense="dense">
      <template v-slot:append>
          <q-btn outline color="indigo"  icon="add" @click="addNewCriteria" >Добавить</q-btn>
        </template>
      </q-input>

 <q-list dense bordered padding class="rounded-borders">
      <q-item clickable v-ripple v-for="(c, idx) in criteriesdata" :key="idx">
        <q-item-section>
        <p> {{c}} - <q-btn round dense flat icon="delete" @click="Remove(idx)" /></p>
        </q-item-section>
      </q-item>

    </q-list>



</template>

<script>
export default {
  data(){
    return{
      newCriteria: null,
    }
  },
  props:{
    criteriesdata: Array,
  },

   methods:{
     addNewCriteria(){
      if(!this.newCriteria){
        console.log('Заполните поле')
      }else{
      this.criteriesdata.push(this.newCriteria)
      this.newCriteria = null
      }
    },
      Remove(e){
      this.criteriesdata.splice(e, 1);
    }
   }

}
</script>

<style>

</style>
