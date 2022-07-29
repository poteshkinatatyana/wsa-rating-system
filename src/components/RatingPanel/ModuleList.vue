<template>


<q-item tag="label" v-ripple v-for="moduleItem in modules" :key="moduleItem.id">
        <q-item-section>
          <q-item-label>{{moduleItem.title}}</q-item-label>
        </q-item-section>
        <q-item-section avatar>
          <q-btn color="indigo" icon="font_download" outline @click="$emit('ViewM', moduleItem)" />
        </q-item-section>
        <q-item-section avatar>
          <q-btn color="indigo" icon="edit" outline @click=" $emit('Edit', moduleItem)" />
        </q-item-section>
         <q-item-section avatar>
          <q-btn color="red" icon="delete" outline @click="$emit('DeleteM', moduleItem.id)" />
        </q-item-section>
      </q-item>


</template>


<script>
export default {

  props:{
    modules: Array,
  },
  methods:{

  }

}
</script>
