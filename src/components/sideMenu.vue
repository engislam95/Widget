<template>
       <q-scroll-area class="fit">
          <q-list padding class="menu-list">

            <q-item  style="margin-bottom:10% ">


            <q-btn outline style="color: black; width:100%" label="New Widget"  icon="add"/>

            </q-item>


            <q-item clickable v-ripple style="margin-bottom:20% ; " >
          
              <q-item-section style="border: 1px dotted black ; padding:5%">
                <div ref="chartdiv" ></div>
              </q-item-section>
            </q-item>

            <q-item  clickable v-ripple>
             
                <q-item-section style="border: 1px dotted black ; padding:5%">
                <div ref="chartdivv" ></div>
                
              </q-item-section>
            </q-item>

    
          </q-list>
        </q-scroll-area>
</template>

<script>
export default {
  name: 'sideMenu',
  props: ['data'],
  methods: {
    markDone() {
      this.$emit('done', this.data);
    }
  }
}
</script>


<style scoped>
</style>