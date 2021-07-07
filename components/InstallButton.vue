<template>
  <div>
   <fab :actions="fabActions"
       @cache="cache"
       @alertMe="alert"
  ></fab>
  </div>
</template>

<script>
import fab from 'vue-fab'
export default {
    components: {
        fab
    },
    data(){
      return {
          bgColor: '#778899',
          position: 'bottom-left',
          fabActions: [
              {
                  name: 'cache',
                  icon: 'cached'
              },
              {
                  name: 'alertMe',
                  icon: 'add_alert'
              }
          ]
      }
  },
  methods:{
      cache(){
          console.log('Cache Cleared');
      },
      alert(){
          alert('Clicked on alert icon');
      }
  }
}
</script>

<style></style>
