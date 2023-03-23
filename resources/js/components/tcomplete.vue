<template>
  <div class="card mb-4">
    <div class="card-body">
      
      <ul class="nav nav-tabs">

        <li class="nav-item">
          <a class="nav-link" href="#">Open</a>
        </li>

        <li class="nav-item">
          <a class="nav-link active cursor-pointer" aria-current="page" v-on:click="getData()">Completed</a>
        </li>

        <form class="d-none d-md-inline-block form-inline ms-auto me-0 me-md-3 my-2 my-md-0">
          <div class="input-group input-group-sm">
            <span class="input-group-text" id="inputGroup-sizing-sm">
              <i id="biru"
                class="fas fa-search">
              </i>
            </span>
            <input class="form-control " type="text" placeholder="Search" @input="onSearch" />
          </div>
        </form>

                                
        <li class="nav-item" style="float: right;">
          <button id="putih" class="btn btn-outline-secondary btn-sm" v-on:click="ExportExcel('tcomplete', 'Tab-complete')"><i id="biru"            
            class="fa-solid fa-file-export"></i>                   
            Export              
          </button>           
        </li>
                     
      </ul>

                            
      <!-- tempat tabel complete -->
                            
      <div class="overflow-auto"> 

        <table id="tcomplete" class="sortable batas table table-hover text-nowrap">

          <thead class="text-bg-secondary">
            <tr>
              <th>Instruction ID
                <div class="btn-group-vertical cursor-pointer" role="group" >
                  <div style="font-size: xx-small; padding-left: 2px;" class="btn1 btn-group-vertical" role="group" aria-label="Vertical radio toggle button group">
                    <i style="color:white" class="bi bi-caret-up sort-up" v-on:click="sortRecordsAsc(0)"></i> 
                    <a style="color:white" class="bi bi-caret-down sort-down" v-on:click="sortRecordsDesc(0)"></a>
                  </div>
                </div>
              </th>
              <th >Link To 
                <div class="btn-group-vertical cursor-pointer" role="group">
                  <div style="font-size: xx-small; padding-left: 5px;" class="btn2 btn-group-vertical" role="group" aria-label="Vertical radio toggle button group">
                    <i style="color:white" class="bi bi-caret-up sort-up" v-on:click="sortRecordsAsc(1)"></i> 
                    <a style="color:white" class="bi bi-caret-down sort-down" v-on:click="sortRecordsDesc(1)"></a>
                  </div>
                </div>
              </th>
              <th>Instruction Type
                <div class=" btn-group-vertical cursor-pointer" role="group">
                  <div style="font-size: xx-small; padding-left: 5px;" class="btn3 btn-group-vertical" role="group" aria-label="Vertical radio toggle button group">
                    <i style="color:white" class="bi bi-caret-up sort-up" v-on:click="sortRecordsAsc(2)"></i> 
                    <a style="color:white" class="bi bi-caret-down sort-down" v-on:click="sortRecordsDesc(2)"></a>
                  </div>
                </div>
              </th>
              <th>Issued To
                <div class=" btn-group-vertical cursor-pointer" role="group">
                  <div style="font-size: xx-small; padding-left: 5px;" class="btn4 btn-group-vertical" role="group" aria-label="Vertical radio toggle button group">
                    <i style="color:white" class="bi bi-caret-up sort-up" v-on:click="sortRecordsAsc(3)"></i> 
                    <a style="color:white" class="bi bi-caret-down sort-down" v-on:click="sortRecordsDesc(3)"></a>
                  </div>
                </div>
              </th>
              <th>Issued Date
                <div class=" btn-group-vertical cursor-pointer" role="group">
                  <div style="font-size: xx-small; padding-left: 5px;" class="btn5 btn-group-vertical" role="group" aria-label="Vertical radio toggle button group">
                    <i style="color:white" class="bi bi-caret-up sort-up" v-on:click="sortRecordsAsc(4)"></i> 
                    <a style="color:white" class="bi bi-caret-down sort-down" v-on:click="sortRecordsDesc(4)"></a>
                  </div>
                </div>
              </th>
              <th>Attention Of
                <div class=" btn-group-vertical cursor-pointer" role="group">
                  <div style="font-size: xx-small; padding-left: 5px;" class="btn6 btn-group-vertical" role="group" aria-label="Vertical radio toggle button group">
                    <i style="color:white" class="bi bi-caret-up sort-up" v-on:click="sortRecordsAsc(5)"></i> 
                    <a style="color:white" class="bi bi-caret-down sort-down" v-on:click="sortRecordsDesc(5)"></a>
                  </div>
                </div>
              </th>
              <th>Quotation No.
                <div class=" btn-group-vertical cursor-pointer" role="group">
                  <div style="font-size: xx-small; padding-left: 5px;" class="btn7 btn-group-vertical" role="group" aria-label="Vertical radio toggle button group">
                    <i style="color:white" class="bi bi-caret-up sort-up" v-on:click="sortRecordsAsc(6)"></i> 
                    <a style="color:white" class="bi bi-caret-down sort-down" v-on:click="sortRecordsDesc(6)"></a>
                  </div>
                </div>
              </th>
              <th>Customer PO
                <div class=" btn-group-vertical cursor-pointer" role="group">
                  <div style="font-size: xx-small; padding-left: 5px;" class="btn8 btn-group-vertical" role="group" aria-label="Vertical radio toggle button group">
                    <i style="color:white" class="bi bi-caret-up sort-up" v-on:click="sortRecordsAsc(7)"></i> 
                    <a style="color:white" class="bi bi-caret-down sort-down" v-on:click="sortRecordsDesc(7)"></a>
                  </div>
                </div>
              </th>
              <th style="text-align: center;">Status
                <div class=" btn-group-vertical cursor-pointer" role="group">
                  <div style="font-size: xx-small; padding-left: 5px;" class="btn9 btn-group-vertical" role="group" aria-label="Vertical radio toggle button group">
                    <i style="color:white" class="bi bi-caret-up sort-up" v-on:click="sortRecordsAsc(8)"></i> 
                    <a style="color:white" class="bi bi-caret-down sort-down" v-on:click="sortRecordsDesc(8)"></a>
                  </div>
                </div>
              </th>
            </tr>
          </thead>
                                
          <tbody class="cursor-pointer">             
            <tr v-for="(item, index) in items" v-bind:key="index">             
              <td> {{ item[0] }}</td>
              <td> {{ item[1] }}</td>
              <td class="mid" >
                <i v-if="item[2]=='LI'" class="bi bi-truck icon"></i>
                <i v-else class="bi bi-person-fill-gear icon"></i>
                {{ item[2] }}
              </td>
              <td> {{ item[3] }}</td>
              <td> {{ item[4] }}</td>
              <td> {{ item[5] }}</td>
              <td> {{ item[6] }}</td>
              <td> {{ item[7] }}</td>
              <td>
                <button id="btn-cancel" v-if="item[8]=='Completed'" class="btn btn-success badge badge-pill bg-success">{{ item[8] }}</button>
                <!-- <button style="font-size: x-small;" id="btn-cancel" v-if="item[8]=='Completed'" class="btn btn-success btn-sm">{{ item[8] }}</button> -->
                
                  <p style="margin-bottom: 0px; position:relative" v-else>
                    <button id="btn-cancel" class="btn btn-secondary badge badge-pill bg-secondary">{{ item[8] }}
                  <a href="#" data-bs-toggle="popover" data-bs-placement="top"
                                        data-bs-content="Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas" 
                                        style="
                                                position: absolute;
                                                margin-left: 10px;
                                                margin-top: -1px;
                                                background-color:#0F6EC4
                                                border: 1px solid black;
                                                border-radius: 50%;
                                                width: 15px;
                                                font-size: 12px;
                                                text-align: center;
                                                text-decoration: none;
                                                color: white;
                                            ">i</a>
                
                </button>
              </p>
              </td>
              <!-- <td v-for="(rowItem, rowIndex) in item" v-bind:key="rowIndex">                           
                {{ rowItemb }}                       
              </td>         -->
            </tr>                      
          </tbody>
                          
        </table>
                        
      </div>
                       
    </div> 
  </div>
</template>

<script>
import { mapGetters } from 'vuex'

const performSearch = (items, term)=> {
  const results = items.filter(item=>item.join(" ").toLowerCase().includes(term.toLowerCase()))
  return results;
}

var popoverTriggerList = [].slice.call(
            document.querySelectorAll('[data-bs-toggle="popover"]')
        );
        var popoverList = popoverTriggerList.map(function (
            popoverTriggerEl
        ) {
            return new bootstrap.Popover(popoverTriggerEl);
        });


export default {
  
  computed: {
    ...mapGetters({
      list :'example/getData'
    })
  },

  mounted (){
    this.$store.dispatch("example/getAllData");
  },

    
  methods:{
    addToggleIconListener(buttonClass) {
        const button = document.querySelector(buttonClass);
            button.addEventListener("click", function () {
                const icon = button.querySelector("i");
                const icon2 = button.querySelector("a");
                  icon.classList.remove("bi-caret-up");
                  icon.classList.add("bi-caret-up-fill");
                  icon2.classList.remove("bi-caret-down-fill");
                  icon2.classList.add("bi-caret-down");
            });
    },
    addToggleIconListener2(buttonClass) {
        const button = document.querySelector(buttonClass);
            button.addEventListener("click", function () {
                const icon = button.querySelector("i");
                const icon2 = button.querySelector("a");
                  icon.classList.remove("bi-caret-up-fill");
                  icon.classList.add("bi-caret-up");
                  icon2.classList.remove("bi-caret-down");
                  icon2.classList.add("bi-caret-down-fill");
            });
    },
        
    getData(){
      this.items=[...this.list];
    },
      
    ExportExcel(tableID, filename = ''){
      var downloadLink;
      var dataType = 'application/vnd.ms-excel';
      var tableSelect = document.getElementById(tableID);
      var tableHTML = tableSelect.outerHTML.replace(/ /g, '%20');
   
      filename = filename?filename+'.xls':'excel_data.xls';
   
      downloadLink = document.createElement("a");
    
      document.body.appendChild(downloadLink);
    
      if(navigator.msSaveOrOpenBlob){
        var blob = new Blob(['\ufeff', tableHTML], {
          type: dataType
        });
        navigator.msSaveOrOpenBlob( blob, filename);
      }

      else{
        downloadLink.href = 'data:' + dataType + ', ' + tableHTML;
   
        downloadLink.download = filename;
       
        downloadLink.click();
      }

    },
      
    onSearch (e){
        
      this.term =e.target.value;
        
      this.items=performSearch(this.list, this.term);
      
    },

    sortRecordsAsc(index){
      this.addToggleIconListener(".btn1");
      this.addToggleIconListener(".btn1");
      this.addToggleIconListener(".btn2");
      this.addToggleIconListener(".btn3");
      this.addToggleIconListener(".btn4");
      this.addToggleIconListener(".btn5");
      this.addToggleIconListener(".btn6");
      this.addToggleIconListener(".btn7");
      this.addToggleIconListener(".btn8");
      this.addToggleIconListener(".btn9");
        this.items=this.items.sort(
          (itemA, itemB) => {
          return itemB[index]<(itemA[index]) ? 1 : -1;
      }
      )
    },

    sortRecordsDesc(index){
      this.addToggleIconListener2(".btn1");
      this.addToggleIconListener2(".btn2");
      this.addToggleIconListener2(".btn3");
      this.addToggleIconListener2(".btn4");
      this.addToggleIconListener2(".btn5");
      this.addToggleIconListener2(".btn6");
      this.addToggleIconListener2(".btn7");
      this.addToggleIconListener2(".btn8");
      this.addToggleIconListener2(".btn9");
        this.items=this.items.sort(
          (itemA, itemB) => {
           return itemA[index]<(itemB[index]) ? 1 : -1;
      }
      )
    },
  },
    
  data() {
    return {
      term:'',
      fields: [
      "Instruction ID",
      "Link To",
      "Instruction Type",
      "Issued To",
      "Issued Date",
      "Attention Of",
      "Quotation No.",
      "Customer PO",
      "Status"
      ],    
      items:[],
      sortIndex:null,
      sortDirection:null
    }
  }
}
</script>

<style>

</style>