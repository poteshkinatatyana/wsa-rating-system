<template>
<div>

<div class="field has-addons">
              <div class="control">
                <input class="input" type="text" v-model="data"  :disabled="! inEdit" />
              </div>
              <div class="control">
                <button class="button is-info" @click="edit">{{buttonLabel}}</button>
              </div>
            </div>

</div>
</template>

<script>
export default {
data(){
  return{
  inEdit: false,
      buttonLabel: 'edit',

  }
},
props:{
  data: String
},
methods:{
 edit() {
      this.inEdit ? this.inEdit = false : this.inEdit = true;
      this.buttonLabel = this.inEdit ? this.buttonLabel = 'save' : this.buttonLabel = 'edit';

    }
}
}
</script>

<style>

</style>
