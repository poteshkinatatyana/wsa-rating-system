<template>

    <!-- {{modules}} -->



  <navbar @ClickAddModule="bar = true" class="q-mb-lg" @ChangeTitle="AddTitleCompetention" @NewTemplate="NewTemplate" @SaveTempalte="SaveTempalte" @DownloadTemplate="DownloadTemplate"/>
<q-scroll-area style="height: 100%; max-width: 100%;">
  <q-splitter
      v-model="splitterModel"
      style="height: 70vh"
    >

      <template v-slot:before>
        <div class="q-pa-md">
          <div class="text-h4 q-mb-lg">Список модулей</div>
          <module-list v-if="modules.length > 0" :modules="modules" @Edit="EditModule" @ViewM="ViewModuleMode" @DeleteM="DeleteModule"/>
        </div>
      </template>

      <template v-slot:separator>
        <q-btn color="indigo" text-color="white" size="10px" icon="drag_indicator" style="width: 15px; height: 40px;" />
      </template>

      <template v-slot:after>
        <div class="q-pa-lg">
          <div class="text-h4 q-mb-md">Обзор</div>
          <view-module v-if="viewmode  && !edit" :viewdata="viewmode"/>
         <edit-module v-if="edit" :editmode="editmode" @SaveModule="SaveModule" @CancelModule="CancelModule"/>
        </div>
      </template>

    </q-splitter>
</q-scroll-area>


  <add-module-dialog :module="module" :bar="bar" @AddModule="AddNewModule" @BarFalse="bar = null"/>

</template>

<script>

import ModuleList from 'src/components/RatingPanel/ModuleList.vue'
import EditModule from 'src/components/RatingPanel/EditModule.vue'
import Navbar from 'src/components/RatingPanel/Navbar.vue'
import AddModuleDialog from 'src/components/RatingPanel/AddModuleDialog.vue'
import ViewModule from 'src/components/RatingPanel/ViewModule.vue'
import { ref } from 'vue'

export default {
  components:{
   ModuleList,EditModule,Navbar,AddModuleDialog,ViewModule
  },
    data(){
    return{
      viewmode: null,
      titlecompetetion: null,
      splitterModel: ref(30),
      bar: ref(false),
      edit: null,
      editmode: null,
      module:{
        id: Date.now(),
        title: 'title',
        criteries:[],
        score:[]
      },
      modules: [],
      defaultdataeditmodules: null
    }
  },
    mounted() {
    if (localStorage.modules) {
      this.modules = JSON.parse(localStorage.getItem("modules")) || [];
      // this.competenciesTitle = localStorage.getItem("competenciesTitle");
    }
  },
  methods:{
    AddTitleCompetention(data){
      this.titlecompetetion = data
    },
    AddNewModule(){
      let newModule ={
        id: Date.now(),
        title: this.module.title,
        criteries: this.module.criteries,
        score: this.module.score
      }
      this.modules.push(newModule)

      this.module.id = Date.now();
      this.module.title = "title"
      this.module.criteries = []
      this.module.score = []
    },
    EditModule(module){
      this.edit = true;
      this.editmode = module;
      this.defaultdataeditmodules = JSON.parse(JSON.stringify(this.modules));
    },
    ViewModuleMode(module){
      this.viewmode = module;
       this.edit = null;
    },
    SaveModule(){
      this.edit = null;
    },
     CancelModule(){
     this.modules = this.defaultdataeditmodules;
      this.edit = null;
    },
    DeleteModule(module){
      console.log(module)
     this.modules = this.modules.filter((item) => item.id !== module);
    },
    SaveTempalte() {
      const parsed = JSON.stringify(this.modules);
      localStorage.setItem("modules", parsed);
      // localStorage.setItem("competenciesTitle", this.competenciesTitle);

      console.log("ff");
    },
    NewTemplate() {
      localStorage.clear();
      window.location.reload();
    },
    DownloadTemplate(){

      let modulesParse = [];

      let title;
      let criteries;
      let criteriascore;
      let item;

            let ipt = `script`;

      let scr = `<${ipt}>


var datainput

var outresult
var score = 0

document.querySelectorAll('.modulesbody').forEach(module => module.addEventListener('click', function(e) {
  e.preventDefault()

  datainput =   this.getElementsByClassName("form-select")
  btnresult =  this.querySelector('.btn');
  outresult = this.querySelector('.out');

  getSumSelectValue(datainput)




}));


const getSumSelectValue = selects => {
  let result = 0;
  for (const select of selects) {
    result += Number(select[select.selectedIndex].value);
  }
  return  outresult.textContent = result;
}

function Screenshot(){
  console.log('vze')
  html2canvas(document.querySelector("#capture")).then(canvas => {
    var my_screen = canvas;

			document.getElementById("result").appendChild(my_screen);
    // document.body.appendChild(canvas)

});
}


               </${ipt}>

               <${ipt} src="http://html2canvas.hertzen.com/dist/html2canvas.min.js"></${ipt}>
               `;


               var modulesHtmlafter = `
                 <!doctype html>
<html lang="ru">
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-1BmE4kWBq78iYhFldvKuhfTAU6auU8tT94WrHftjDbrCEXSU1oBoqyl2QvZ6jIW3" crossorigin="anonymous">
    <title>${this.competenciesTitle}</title>
  </head>
  <body>


   <div class="container pt-2" id="capture">



               `

               var modulesHtmlbefore = `
                  ${scr}


<style>
.hide{
  display:none !important;
}
</style>

</div>
  <div class="container mb-2 mt-2" >
  <center>
   <button class="btn btn-dark" onclick="Screenshot()">Сохранить результат</button>

<small style="color: grey; margin-top: 25px; margin-bottom: 25px;">Скачать можно кликнув правой кнопкой мышью -> "Сохранить как..."⤵️</small>

<div id="result"  ></div>
</center>
<style>
#result canvas{
width: 500px ! important; height: 350px !important; object-fit: contain;
}
</style>
  </div>

    </body>
</html>
               `

         for (let index = 0; index < this.modules.length; index++) {
        title = this.modules[index].title;
        criteries = this.modules[index].criteries;
        criteriascore = this.modules[index].score;
             var modulesHtml = `


           <h3 class="text-danger mt-4 mb-3">Модуль : ${title}</h3>

    <div class="p-5 border modulesbody" id="modulesbody">
        <table class="table ">
            <thead>
              <div>

                <th scope="col">Критерий</th>
                <th scope="col">Оценка</th>

              </div>
            </thead>
            <tbody>
              <tr>




                <td class="hide">${(item = criteriascore.map((ell, idx) => {
                    return `<option value="` + idx + `"  >` + ell + `</option>`;
                  })
                  .join(""))}</td>

               ${criteries.map((el) => {
                   return (
                     `<div class="row"><div class="col-6 col"><ul class="list-group "> <li class="list-group-item">` +
                     el +
                     `</li>` +
                     `</ul></div> ` +
                     `<div class="col col-6 select-div" > <select  class="form-select " aria-label="Default select example"> ` +
                     item +
                     `</select></div> </div> `
                   );
                 })
                 .join("")}

                  </tr>
            </tbody>
          </table>
          <center>


          <h3>Итоговый результат за модуль - <span class="out"> <strong> </strong> </span> </h3>

          </center>
    </div>

  `;

    modulesParse.push(modulesHtml)


      }

      modulesParse.push(modulesHtmlbefore)

      modulesParse.unshift(modulesHtmlafter)

const parsedd = JSON.stringify(this.modules);
      const data = modulesParse.join("");
      const blob = new Blob([data], { type: "text/plain" });
      const e = document.createEvent("MouseEvents"),
        a = document.createElement("a");
      a.download = `${this.titlecompetetion}.html`;
      a.href = window.URL.createObjectURL(blob);
      a.dataset.downloadurl = ["text/json", a.download, a.href].join(":");
      e.initEvent(
        "click",
        true,
        false,
        window,
        0,
        0,
        0,
        0,
        0,
        false,
        false,
        false,
        false,
        0,
        null
      );
      a.dispatchEvent(e);
    }


  }

}
</script>

<style>

</style>
