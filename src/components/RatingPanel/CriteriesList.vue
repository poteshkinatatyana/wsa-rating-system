<template>


 <q-input bottom-slots  v-model="newCriteria" label="Добавить критерий"  :dense="dense">
      <template v-slot:append>
          <q-btn round dense flat icon="add" @click="addNewCriteria" />
        </template>
      </q-input>



     <q-list bordered separator  v-for="criteria in criteriesdata" :key="criteria">
      <q-item clickable v-ripple>
        <q-item-section> {{criteria}}</q-item-section>
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
  methods: {
    addNewCriteria(){
      if(!this.newCriteria){
        console.log('Заполните поле')
      }else{
      this.criteriesdata.push(this.newCriteria)
      this.newCriteria = null
      }
    }

  }

}
</script>

<style>

</style>
