<template>

    <div>
       <h1>Home page</h1>
        
        <b-button v-if="deferredPrompt"
            v-b-modal.modal>
                Install app
        </b-button>
       
        <b-modal id="modal" color="info" dark class="text-left" >
            Install the app on your phone for better experience.
            <div slot="modal-footer" >
                <b-button  @click="dismiss">Close Modal</b-button>
                <b-button  @click="install" >Install</b-button>
            </div>
        </b-modal>
    </div>
  
</template>

<script>
export default {
    data() {
        return {
            deferredPrompt : null
        }
    },
   
    
    mounted() {
        window.addEventListener("beforeinstallprompt", e => {
            e.preventDefault();
            this.deferredPrompt = e;
        });
        window.addEventListener("appinstalled", () => {
            this.deferredPrompt = null;
        });
    },

    methods: {
        async dismiss() {
            this.deferredPrompt = null;
            this.$root.$emit('bv::hide::modal', 'modal', '#btnShow')
        },

        async install(){
            this.deferredPrompt.prompt();
            this.$root.$emit('bv::toggle::modal', 'modal', '#btnToggle')
        },
    }
}
</script>

<style> 


</style>