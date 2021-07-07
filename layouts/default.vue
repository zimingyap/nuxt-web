<template>
  <div>
      <AppHeader/>
    
    <Nuxt keep-alive/>
    <!-- <div variant='danger' v-if="$nuxt.isOffline">{{offlineToast('danger')}}</div>
    <div v-if="$nuxt.isOffline"> <h1>offline</h1> </div> -->
    
  </div>
</template>
<script>
import AppHeader from '../components/AppHeader..vue';
export default {

    components: {
        AppHeader,
        
    },
    computed: {
        connectionStatus() {
        return this.$nuxt.isOffline
        },
    },
    watch: {
    connectionStatus(offline) {
      if (offline) {

        // hide the online toast if it exists
        this.$bvToast.hide('online')

        // create a new toast for offline notification
        // that doesn't hide on its own
        this.$bvToast.toast('You are now offline', {
          id: 'offline',
          toaster: 'b-toaster-bottom-right',
          noCloseButton: true,
          solid: true,
          noAutoHide: true,
          variant: 'danger',
        })
      } else {

        // hide the offline toast if it exists
        this.$bvToast.hide('offline')

        // create a new toast for online notification
        // that auto hides after a given time
        this.$bvToast.toast('You are now online', {
          id: 'online',
          toaster: 'b-toaster-bottom-right',
          noCloseButton: true,
          solid: true,
          autoHideDelay: 5000,
          variant: 'success',
        })
      }
    },
  },
   
}
</script>
<style>

</style>
