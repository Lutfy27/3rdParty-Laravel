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

        <table id="tcomplete" class="batas table table-hover text-nowrap">

          <thead class="text-bg-secondary">
            <tr class="cursor-pointer">
              <!-- <th v-for="(field, index) in fields" v-bind:key="index" v-on:click="sortRecords(index)">{{ field }}
                <div class="btn-group-vertical btn1" role="group" aria-label="Vertical button group">
                  <i id="myDIV1" style="margin-bottom: 0%; color:white" class="bi bi-caret-up"></i>
                  <i id="myDIV2" style="margin-top: 0%; color:white" class="bi bi-caret-down"></i>
                </div>
              </th>
              <th  v-on:click="sortRecords(index)">Link To 
                <div class="btn-group-vertical" role="group" aria-label="Vertical button group">
                  <i id="myDIV1" style="margin-bottom: 0%; color:white" class="bi bi-caret-up"></i>
                  <i id="myDIV2" style="margin-top: 0%; color:white" class="bi bi-caret-down"></i>
                </div>
              </th>
              <th  v-on:click="sortRecords(index)">Instruction Type
                <div class="btn-group-vertical" role="group" aria-label="Vertical button group">
                  <i id="myDIV1" style="margin-bottom: 0%; color:white" class="bi bi-caret-up"></i>
                  <i id="myDIV2" style="margin-top: 0%; color:white" class="bi bi-caret-down"></i>
                </div>
              </th>
              <th  v-on:click="sortRecords(index)">Issued To
                <div class="btn-group-vertical" role="group" aria-label="Vertical button group">
                  <i id="myDIV1" style="margin-bottom: 0%; color:white" class="bi bi-caret-up"></i>
                  <i id="myDIV2" style="margin-top: 0%; color:white" class="bi bi-caret-down"></i>
                </div>
              </th>
              <th  v-on:click="sortRecords(index)">Issued Date
                <div class="btn-group-vertical" role="group" aria-label="Vertical button group">
                  <i id="myDIV1" style="margin-bottom: 0%; color:white" class="bi bi-caret-up"></i>
                  <i id="myDIV2" style="margin-top: 0%; color:white" class="bi bi-caret-down"></i>
                </div>
              </th>
              <th  v-on:click="sortRecords(index)">Attention Of
                <div class="btn-group-vertical" role="group" aria-label="Vertical button group">
                  <i id="myDIV1" style="margin-bottom: 0%; color:white" class="bi bi-caret-up"></i>
                  <i id="myDIV2" style="margin-top: 0%; color:white" class="bi bi-caret-down"></i>
                </div>
              </th>
              <th  v-on:click="sortRecords(index)">Quotation No.
                <div class="btn-group-vertical" role="group" aria-label="Vertical button group">
                  <i id="myDIV1" style="margin-bottom: 0%; color:white" class="bi bi-caret-up"></i>
                  <i id="myDIV2" style="margin-top: 0%; color:white" class="bi bi-caret-down"></i>
                </div>
              </th>
              <th  v-on:click="sortRecords(index)">Customer PO
                <div class="btn-group-vertical" role="group" aria-label="Vertical button group">
                  <i id="myDIV1" style="margin-bottom: 0%; color:white" class="bi bi-caret-up"></i>
                  <i id="myDIV2" style="margin-top: 0%; color:white" class="bi bi-caret-down"></i>
                </div>
              </th>
              <th  v-on:click="sortRecords(index)">Status
                <div class="btn-group-vertical" role="group" aria-label="Vertical button group">
                  <i id="myDIV1" style="margin-bottom: 0%; color:white" class="bi bi-caret-up"></i>
                  <i id="myDIV2" style="margin-top: 0%; color:white" class="bi bi-caret-down"></i>
                </div>
              </th> -->

              <th v-for="(field, index) in fields" v-bind:key="index" v-on:click="sortRecords(index)">
                
                {{ field }} 

                <!-- <div class="btn-group-vertical" role="group" aria-label="Vertical radio toggle button group">
                <input type="radio" class="btn-check" name="vbtn-radio" id="vbtn-radio1" autocomplete="off">
                <label class="btn btn-outline-secondary btn-sm" for="vbtn-radio1"><i class="bi bi-caret-up-fill"></i></label>
                <input type="radio" class="btn-check" name="vbtn-radio" id="vbtn-radio2" autocomplete="off">
                <label class="btn btn-outline-secondary btn-sm" for="vbtn-radio2"><i class="bi bi-caret-down-fill"></i></label>
                </div> -->

                <div class="btn-group-vertical" role="group" aria-label="Vertical button group">
                  <i id="myDIV1" style="color:white" class="bi bi-caret-up"></i>
                  <i id="myDIV2" style="color:white" class="bi bi-caret-down"></i>
                </div>
              </th>
            </tr>
          </thead>
                                
          <tbody class="cursor-pointer">              
            <tr v-for="(item, index) in items" v-bind:key="index">             
              <td v-for="(rowItem, rowIndex) in item" v-bind:key="rowIndex">                           
                {{ rowItem }}                       
              </td>        
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

    sortRecords(index){
      console.log(index)

      var element1 = document.getElementById("myDIV1");
      var element2 = document.getElementById("myDIV2");
      if(this.sortIndex === index){
        switch (this.sortDirection){
          case 'asc':
          this.sortDirection='desc';
          element1.classList.remove("bi-caret-up-fill");
          element1.classList.add("bi-caret-up");
          element2.classList.remove("bi-caret-down");
          element2.classList.add("bi-caret-down-fill");
          break;
          case 'desc':
          this.sortDirection='asc';
          element1.classList.remove("bi-caret-up");
          element1.classList.add("bi-caret-up-fill");
          element2.classList.remove("bi-caret-down-fill");
          element2.classList.add("bi-caret-down");
          break;
        }
      }

      else {
        this.sortDirection='asc'
        element1.classList.remove("bi-caret-up");
        element1.classList.add("bi-caret-up-fill");
        element2.classList.remove("bi-caret-down-fill");
        element2.classList.add("bi-caret-down");
      }
      this.sortIndex=index;
      if (!this.sortDirection){
        this.items=performSearch(this.list, this.term);
        return;
      }

      this.items=this.items.sort(
      (itemA, itemB) => {
        if (this.sortDirection === 'desc'){
          return itemA[index]<(itemB[index]) ? 1 : -1;
        }
        return itemB[index]<(itemA[index]) ? 1 : -1;
      }
      )
    }
  },
    
  data() {
    return {
      sortDirection: "asc",
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