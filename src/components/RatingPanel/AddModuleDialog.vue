<template>



      <q-dialog v-model="bar" persistent>
        <q-card style=" height: 600px; max-width: 1500px;width:1000px;">
              <q-card-section class="row items-center q-pb-none">
                <div class="text-h6">Добавления модуля</div>
                <q-space />
                <q-btn icon="close" @click="BarNull" flat round dense  />
              </q-card-section>

              <q-card-section >

                  <add-module class="q-pt-lg" :module="module" @AddNewModule="NewModule"/>

              </q-card-section>
            </q-card>
    </q-dialog>

</template>

<script>

import AddModule from 'src/components/RatingPanel/AddModule.vue'

export default {
components:{AddModule},
  data(){
    return{

    }
  },
props:{
  module:Object,
  bar: Boolean
},
methods:{
  NewModule(){
    this.$emit('AddModule')
    this.$emit('BarFalse')
  },
  BarNull(){
     this.$emit('BarFalse')
  }
}
}
</script>

<style scoped>

</style>
