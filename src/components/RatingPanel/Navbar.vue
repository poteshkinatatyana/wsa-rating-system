<template>
   <div class="q-pa-md">
    <q-scroll-area style="height: 130px; max-width: 100%;">
    <q-toolbar class="bg-none text-white font-bold ">
      <img src="~assets/logo.png" style="width:200px; object-fit: cover; margin-right: 20px;" alt="">

        <q-input outline bottom-slots label="Название компетенции" v-model="titlecom"   style="padding-top: 15px; min-width: 350px; text-transform: uppercase;">
        <template v-slot:append>
          <q-btn round dense flat icon="add" @click="ChangeTitle" />
        </template>
      </q-input>

      <q-space />

      <q-tabs v-model="tab" shrink>
        <q-btn label="Добавить модуль" outline class="q-mr-md" color="black" @click="$emit('ClickAddModule')"  />
        <q-btn label="Сохранить шаблон" outline class="q-mr-md" color="black" @click="$emit('SaveTempalte')" />
        <q-btn label="Новый шаблон" outline class="q-mr-md" color="black" @click="$emit('NewTemplate')" />
        <q-btn label="Скачать шаблон" outline color="black" @click="$emit('DownloadTemplate')" />

      </q-tabs>
    </q-toolbar>
    </q-scroll-area>
  </div>
</template>

<script>
export default {

   data(){
     return{
       titlecom: 'Компетенция'
     }

  },
  computed:{
    ChangeTitle(){
      this.$emit('ChangeTitle', this.titlecom )
    }
  }



}
</script>

<style>

</style>
