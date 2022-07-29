<template>

<h3>
  <b>{{viewdata.title}}</b>
</h3>

 <q-list dense bordered padding class="rounded-borders">
      <q-item clickable v-ripple v-for="criteria in viewdata.criteries" :key="criteria">
        <q-item-section>
         {{criteria}}
        </q-item-section>
      </q-item>

    </q-list>

    <br>

     <q-list dense bordered padding class="rounded-borders">
      <q-item clickable v-ripple v-for="(score, idx) in viewdata.score" :key="idx">
        <q-item-section>
         <p>Описание оценки критерия <b>{{idx}}</b> - {{score}}</p>
        </q-item-section>
      </q-item>

    </q-list>



</template>

<script>

export default {

  props:{
    viewdata: Object
  }

}
</script>

<style>

</style>
