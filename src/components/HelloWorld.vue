<template>
  <div class="hello" >

    <!-- ref="chartdiv"  -->

     <q-layout view="hHh Lpr lff"  style="height: 100%" class=" rounded-borders">
      <q-header elevated class="bg-black" style="text-align:left !important">
        <q-toolbar  class="glossy">
          <!-- <q-btn flat @click="drawer = !drawer" round dense icon="menu" /> -->
          <q-toolbar-title>Dashboard</q-toolbar-title>
            <q-avatar>
            <img src="https://cdn.quasar.dev/img/avatar.png">
          </q-avatar>
           <q-btn-dropdown stretch flat label="Islam Ahmed">
              <q-list>
                <!-- <q-item-label header>Folders</q-item-label> -->
                <q-item style="border-bottom:1px dotted grey" clickable v-close-popup tabindex="0">
                  <q-item-section avatar>
                    <q-avatar icon="account_circle" style="font-size:50px" text-color="black" />
                  </q-item-section>
                  <q-item-section>
                    <q-item-label>Profile</q-item-label>
                  </q-item-section>
                  
                </q-item>

                <q-item  style="border-bottom:1px solid grey" clickable v-close-popup tabindex="0">
                  <q-item-section avatar>
                    <q-avatar icon="lock"  style="font-size:50px" text-color="black" />
                  </q-item-section>
                  <q-item-section>
                    <q-item-label>Log out</q-item-label>
                  </q-item-section>
               
                </q-item>
               
              </q-list>
            </q-btn-dropdown>

        </q-toolbar>

        <div class="underHeader" style="background:#fff ; height:70px ; width:100%">
        <h5 style="color:black ; margin:0% ; padding:1%"> Drew's Analytics Dashboard <q-icon name="edit" color="grey" /></h5>
      </div>
<!-- 
        <div class=" text-right">
              <div class="header-actions">
                <el-dropdown>
                  <span class="el-dropdown-link">
                    <div class="el-dropdown-link-body">
                     
                      <span style="color:#68D81D"> Welcome , </span>
                      <span >Islam Ahmed</span>
                      <i class="el-icon-arrow-down el-icon--right"></i>
                    </div>
                  </span>
                  <el-dropdown-menu slot="dropdown">
                  
                    <el-dropdown-item   style="border-bottom: 1px dotted grey">
                      <i class="el-icon-fa-user-o"></i> &#160;
                       <span> Update my information  </span>
                       <q-icon  name="img:/images/error.svg "  style="width:10%"/>
                    </el-dropdown-item>
                     <el-dropdown-item style="border-bottom: 1px dotted grey">
                      <i class="el-icon-fa-lock"></i> &#160;
                     Change my password
                    </el-dropdown-item>
                    <el-dropdown-item  >
                      <i class="el-icon-fa-sign-out"></i> &#160;
                     Sign Out
                    </el-dropdown-item>
                  </el-dropdown-menu>
                </el-dropdown>

                
              </div>
        </div> -->
      </q-header>

      

      <q-drawer
        v-model="drawer"
        show-if-above
        :width="300"
        :breakpoint="500"
        bordered
        style="background:#fff"
      >
          <q-scroll-area class="fit">
          <q-list padding class="menu-list">

            <q-item  style="margin-bottom:10% ">


            <q-btn outline style="color: black; width:100%" label="New Widget"  icon="add" @click="addWidget"/>

            </q-item>


            <q-item clickable v-ripple style="margin-bottom:20% ; " >
          
              <q-item-section style="border: 1px dotted black ; padding:5%">
                <div id="droppable_area" @dragover="allowDrop($event)" @drop="drop($event)">

                    <div  draggable="true" @dragstart="drag($event)" id="chartdiv" ref="chartdiv" ></div>

                </div>
              </q-item-section>
            </q-item>

            <q-item  clickable v-ripple>
             
                <q-item-section style="border: 1px dotted black ; padding:5%">
                  <div id="droppable_area" @dragover="allowDrop($event)" @drop="drop($event)">
                <div draggable="true" @dragstart="drag($event)" id="chartdivv" ref="chartdivv" ></div>
                  </div>
                
            </q-item-section>

            </q-item>

    
          </q-list>
        </q-scroll-area>
      </q-drawer>

      <q-page-container>
        <q-page padding class="bg-grey-3" style="text-align:left !important ">
          <h5 style="color:black ; margin:0% ; padding:0% ; margin-bottom:2%"> Drag a widget into an open dashboard slot. </h5>

           <q-tabs
            v-model="tab"
            align="justify"
            narrow-indicator
            class="q-mb-lg"
            
          >
          <q-tab class="text-black" name="mails" label="Layout Resizable" />
          <q-tab class="text-black" name="alarms" label="Layout Draggable and Resizable " />
       
         </q-tabs>

      <div class="q-gutter-y-sm">
        <q-tab-panels
          v-model="tab"
          animated
          transition-prev="scale"
          transition-next="scale"
          class="bg-transparent text-black text-center"
        >
          <q-tab-panel name="mails" style="height:100vh">
              <div class="FixedArea">
                <div class="container row" style="margin-bottom:5%">
                  <div class="col-lg-6" style="cursor:pointer" >
                    <div style="position:relative ;  resize: both; overflow: auto;" id="droppable_areaa" class="droppable_areaa" @dragover="allowDrop($event)" @drop="drop($event)" > 
                      <q-icon name="add_circle" style=" color: grey; opacity: 0.5; top: 45%; left: 0%; font-size: 39px;" ></q-icon> 
                    </div>
                  </div>
                  <div class="col-lg-6" style="cursor:pointer">
                    <div style="position:relative ;  resize: both; overflow: auto;" class="droppable_areaa" @dragover="allowDrop($event)" @drop="drop($event)" > 
                      
                      <q-icon name="add_circle" style=" color: grey; opacity: 0.5; top: 45%; left: 0%; font-size: 39px;" ></q-icon> 
                    </div>
                  </div>
                </div>

                <div class="row" >
                  <div class="col-lg-6" id="leftSide">
                    <div class="row droppable_areaaa"  id="aboveLeftSide"  style="margin-right:1%">
                      <div v-for="(item , key ) in items" :key="key" class="col-lg-4" style="cursor:pointer">
                        <div style="position:relative ;  resize: both; overflow: auto; margin-bottom:2%" id="droppable_areaa" class="droppable_areaa" @dragover="allowDrop($event)" @drop="drop($event,key)" > 
                          <!-- <q-icon @click="removeWidgett(item)" name="delete" style=" color: grey; opacity: 0.5; top: 0%; left: 85%; font-size: 39px;" ></q-icon>  -->
                          <q-icon :id="key" name="add_circle" style=" color: grey; opacity: 0.5; top: 45%; left: 0%; font-size: 39px;" ></q-icon> 
                        </div>
                      </div>
                  </div>
                  </div>
                  <div class="col-lg-6">
                    <div class="row droppable_areaaa"  id="aboveLeftSide">   
                          <div v-for="(item , key )  in itemsUnder" :key="key" class="col-lg-6" :id="key+100" style="cursor:pointer ">
                        
                            <div style="position:relative ; height:600px ; resize: both; overflow: auto;" id="droppable_areaa" class="droppable_areaa" @dragover="allowDrop($event)" @drop="drop($event,key)" > 
                              <!-- <q-icon @click="removeWidget(item)" name="delete" style=" color: grey; opacity: 0.5; top: 0%; left: 85%; font-size: 39px;" ></q-icon>  -->
                              <q-icon :id="key" name="add_circle" style=" color: grey; opacity: 0.5; top: 45%; left: 0%; font-size: 39px;" ></q-icon> 
                            </div>
                      
                          </div>
                  </div>
                  </div>
                </div>
            </div>
          </q-tab-panel>

          <q-tab-panel name="alarms" style="height:100vh">
              <div class="DraggerArea ">
                <div v-for="(item , key ) in items" :key="key"   style="cursor:pointer ; display:inline-block ; margin-bottom:10% ;">
                  <vue-draggable-resizable :parent="false" >
                    <div  style="cursor:pointer  ; " >
                        <div style="position:relative ;   resize: both; overflow: auto;" id="droppable_areaa" class="droppable_areaa" @dragover="allowDrop($event)" @drop="drop($event)" > 
                          <q-icon name="add_circle" style=" color: grey; opacity: 0.5; top: 45%; left: 0%; font-size: 39px;" ></q-icon> 
                        </div>
                      </div>
                  </vue-draggable-resizable>
                </div>
              </div>
          </q-tab-panel>

      
        </q-tab-panels>

      
  
      </div>

          

         

          <div class="text-right" style="padding:5%" >
            <q-btn color="white" text-color="black" @click="reset()" label="Back" icon="undo" style="margin-right:2% ; text-transform:capitalize"/>
            <q-btn color="primary" label="Finsih"  @click="save()" style=" text-transform:capitalize" />
          </div>


        </q-page> 
      </q-page-container>


    </q-layout>

     <!-- <q-layout view="hHh Lpr lff"  style="height: 100%" class="shadow-2 rounded-borders">
      <q-header elevated class="bg-black">
        <q-toolbar>
          <q-btn flat @click="drawer = !drawer" round dense icon="menu" />
          <q-toolbar-title>Header</q-toolbar-title>
        </q-toolbar>
      </q-header>

      <q-drawer
        v-model="drawer"
        show-if-above
        :width="200"
        :breakpoint="500"
      >
        <q-scroll-area class="fit">
          <q-list padding class="menu-list">
            <q-item clickable v-ripple style="margin-bottom:20%">
          

              <q-item-section>
                <div ref="chartdiv" ></div>
              </q-item-section>
            </q-item>

            <q-item  clickable v-ripple>
             
                <q-item-section>
                <div ref="chartdivv" ></div>
                
              </q-item-section>
            </q-item>

    
          </q-list>
        </q-scroll-area>
      </q-drawer>

      <q-page-container>
        <q-page padding>
          <p v-for="n in 15" :key="n">
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Fugit nihil praesentium molestias a adipisci, dolore vitae odit, quidem consequatur optio voluptates asperiores pariatur eos numquam rerum delectus commodi perferendis voluptate?
          </p>
        </q-page>
      </q-page-container>
    </q-layout> -->


   <notifications group="success" />
  </div>
</template>

<script>

import * as am4core from "@amcharts/amcharts4/core";
import * as am4charts from "@amcharts/amcharts4/charts";
import am4themes_animated from "@amcharts/amcharts4/themes/animated";
import VueDraggableResizable from 'vue-draggable-resizable'
import Vue from 'vue'
import Notifications from 'vue-notification'
Vue.use(Notifications)
Vue.component('vue-draggable-resizable', VueDraggableResizable)

am4core.useTheme(am4themes_animated);



export default {
  name: 'HelloWorld',
  props: {
    msg: String
  } ,

  components:{
          
  },

   data () {
    return {
      drawer: false ,
      items: [],
      itemsUnder:[] ,
      tab: 'mails'

      
    }
  },

  created() {
  
  },

  mounted() {

    this.firstOne()
    

    this.secondOne()



  },





  

  beforeDestroy() {
    if (this.chart) {
      this.chart.dispose();
    }


    
  },


  methods:{

    save()
    {
      sessionStorage.setItem('items',JSON.stringify(this.items))
      sessionStorage.setItem('itemsUnder',JSON.stringify(this.itemsUnder))

      this.$notify({
        group: 'success',
         type: 'success',
         speed: 500 ,
        text: 'Layout saved successfully'
      });




    },

    reset()
    {
      if(sessionStorage.getItem('items') )
      {
        this.items = JSON.parse(sessionStorage.getItem('items'))

      }
      if( sessionStorage.getItem('itemsUnder'))
      {
        this.itemsUnder = JSON.parse(sessionStorage.getItem('itemsUnder'))

      }

      else
      {
        this.items = [] ;
         this.itemsUnder = []
      }
      
    },

removeWidget(elementId)
{
  console.log(elementId)
  const index =  this.itemsUnder.indexOf(elementId);
    if (index > -1) {
      this.itemsUnder.splice(index, 1);
    }
},

removeWidgett(elementId)
{
  console.log(elementId)
  const index =  this.items.indexOf(elementId);
    if (index > -1) {
      this.items.splice(index, 1);
    }
},
    addWidget()
    {
      var arr = [];
      let count = 0 ;
      while(arr.length < 10){
          var r = Math.floor(Math.random() * 100) + 1;
          if(arr.indexOf(r) === -1)
          {
            arr.push(r); 
            count = r
          } 
      }
      console.log(count);



        // let aboveLeftSide = document.getElementById('aboveLeftSide')
        if(this.items.length != 6)
        {
          this.items.push(count)
        }
        else
        {

            if(this.itemsUnder.length != 2)
            {
              this.itemsUnder.push(count)
            }

        }

      
       
        


    },

    

    drag($event) {
    console.log('drag start');
    $event.dataTransfer.setData('text', $event.target.id);
},

drop($event,elementId) {
    console.log($event.target);
      console.log(elementId)
      if(document.getElementById(elementId))
      {
        document.getElementById(elementId).remove();

      }
    let area = $event.target;
    let imgId = $event.dataTransfer.getData('text')
    area.appendChild(document.getElementById(imgId));
}, 

allowDrop($event) {
    console.log('drop start');
    $event.preventDefault()
},



    firstOne()
    {

          let chart = am4core.create(this.$refs.chartdiv, am4charts.XYChart);

   chart.hiddenState.properties.opacity = 0; // this creates initial fade-in

chart.data = [
  {
    country: "USA",
    visits: 23725
  },
  {
    country: "China",
    visits: 1882
  },
  {
    country: "Japan",
    visits: 1809
  },
  {
    country: "Germany",
    visits: 1322
  },
  {
    country: "UK",
    visits: 1122
  },
  {
    country: "France",
    visits: 1114
  },
  {
    country: "India",
    visits: 984
  },
  {
    country: "Spain",
    visits: 711
  },
  {
    country: "Netherlands",
    visits: 665
  },
  {
    country: "Russia",
    visits: 580
  },
  {
    country: "South Korea",
    visits: 443
  },
  {
    country: "Canada",
    visits: 441
  }
];

var categoryAxis = chart.xAxes.push(new am4charts.CategoryAxis());
categoryAxis.renderer.grid.template.location = 0;
categoryAxis.dataFields.category = "country";
categoryAxis.renderer.minGridDistance = 40;
categoryAxis.fontSize = 11;

var valueAxis = chart.yAxes.push(new am4charts.ValueAxis());
valueAxis.min = 0;
valueAxis.max = 24000;
valueAxis.strictMinMax = true;
valueAxis.renderer.minGridDistance = 30;
// axis break
var axisBreak = valueAxis.axisBreaks.create();
axisBreak.startValue = 2100;
axisBreak.endValue = 22900;
//axisBreak.breakSize = 0.005;

// fixed axis break
var d = (axisBreak.endValue - axisBreak.startValue) / (valueAxis.max - valueAxis.min);
axisBreak.breakSize = 0.05 * (1 - d) / d; // 0.05 means that the break will take 5% of the total value axis height

// make break expand on hover
var hoverState = axisBreak.states.create("hover");
hoverState.properties.breakSize = 1;
hoverState.properties.opacity = 0.1;
hoverState.transitionDuration = 1500;

axisBreak.defaultState.transitionDuration = 1000;


var series = chart.series.push(new am4charts.ColumnSeries());
series.dataFields.categoryX = "country";
series.dataFields.valueY = "visits";
series.columns.template.tooltipText = "{valueY.value}";
series.columns.template.tooltipY = 0;
series.columns.template.strokeOpacity = 0;

// as by default columns of the same series are of the same color, we add adapter which takes colors from chart.colors color set
series.columns.template.adapter.add("fill", function(fill, target) {
  return chart.colors.getIndex(target.dataItem.index);
});


    },

      secondOne()
  {

    let Secchart = am4core.create(this.$refs.chartdivv, am4charts.RadarChart);

Secchart.data = [{
 "country": "USA",
 "visits": 2025
}, {
 "country": "China",
 "visits": 1882
}, {
 "country": "Japan",
 "visits": 1809
}, {
 "country": "Germany",
 "visits": 1322
}, {
 "country": "UK",
 "visits": 1122
}, {
 "country": "France",
 "visits": 1114
}, {
 "country": "India",
 "visits": 984
}, {
 "country": "Spain",
 "visits": 711
}, {
 "country": "Netherlands",
 "visits": 665
}, {
 "country": "Russia",
 "visits": 580
}, {
 "country": "South Korea",
 "visits": 443
}, {
 "country": "Canada",
 "visits": 441
}];

Secchart.innerRadius = am4core.percent(40)

let categoryAxis = Secchart.xAxes.push(new am4charts.CategoryAxis());
categoryAxis.renderer.grid.template.location = 0;
categoryAxis.dataFields.category = "country";
categoryAxis.renderer.minGridDistance = 60;
categoryAxis.renderer.inversed = true;
categoryAxis.renderer.labels.template.location = 0.5;
categoryAxis.renderer.grid.template.strokeOpacity = 0.08;

let valueAxis = Secchart.yAxes.push(new am4charts.ValueAxis());
valueAxis.min = 0;
valueAxis.extraMax = 0.1;
valueAxis.renderer.grid.template.strokeOpacity = 0.08;

Secchart.seriesContainer.zIndex = -10;


let series = Secchart.series.push(new am4charts.RadarColumnSeries());
series.dataFields.categoryX = "country";
series.dataFields.valueY = "visits";
series.tooltipText = "{valueY.value}"
series.columns.template.strokeOpacity = 0;
series.columns.template.radarColumn.cornerRadius = 5;
series.columns.template.radarColumn.innerCornerRadius = 0;

Secchart.zoomOutButton.disabled = true;

// as by default columns of the same series are of the same color, we add adapter which takes colors from chart.colors color set
series.columns.template.adapter.add("fill", (fill, target) => {
 return Secchart.colors.getIndex(target.dataItem.index);
});

setInterval(()=>{
 am4core.array.each(Secchart.data, (item)=>{
   item.visits *= Math.random() * 0.5 + 0.5;
   item.visits += 10;
 })
 Secchart.invalidateRawData();
}, 2000)

categoryAxis.sortBySeries = series;

Secchart.cursor = new am4charts.RadarCursor();
Secchart.cursor.behavior = "none";
Secchart.cursor.lineX.disabled = true;
Secchart.cursor.lineY.disabled = true;

    
  }

  },





}
</script>



<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>

<style >
.q-layout__shadow:after
{
  box-shadow: none !important ;
      border-bottom: 1px solid #80808069;

}
#droppable_areaa {
    border: 1px dotted #000;
    height: 300px;
    background: #fff; 
    opacity: 0.8;
    
    padding: 20px 0;
}
.col-lg-4 .droppable_areaa
{
    border: 1px dotted #000;
    background: #fff; 
    margin-right: 2% ;
    width: 31%;

    opacity: 0.8;

}
.col-lg-6 .droppable_areaa
{
    border: 1px dotted #000;
    background: #fff; 
    margin-right: 2% ;
    width: 47%;

    opacity: 0.8;

}
.col-lg-6 .col-lg-4 .droppable_areaa
{
    border: 1px dotted #000;
    background: #fff; 
    margin-right: 2% ;
    width: 31%;

    opacity: 0.8;

}
.col-lg-6 .droppable_areaaa
{
  /* border: 1px dotted #000; */
    /* background: #fff;  */
    margin-right: 2% ;
    width: 47%;

    opacity: 0.8;
}

.col-lg-6 .col-lg-4 .droppable_areaaa
{
  /* border: 1px dotted #000; */
    /* background: #fff;  */
    margin-right: 2% ;
    width: 31%;

    opacity: 0.8;
}
#droppable_area {
    border: 1px dotted #000;
    /* height: 500px;
    width: 500px; */
    padding: 20px 0;
}

.container
{
  display: block ;
  margin: 0 auto ;
}
.col-lg-4
{
  display: contents ;
}
/* .col-lg-3
{
  display: contents ;
} */
.col-lg-6
{
  display: contents ;

}

.vue-notification {
  padding: 20px;
  margin: 0 5px 5px;
 
  font-size: 15px;
 
 
}
</style>
