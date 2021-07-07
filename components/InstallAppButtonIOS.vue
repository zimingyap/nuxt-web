<template>
<div>
  <v-btn depressed block v-b-modal.modal-1>
    <svg
        xmlns="http://www.w3.org/2000/svg"
        width="16"
        height="16"
        fill="currentColor"
        class="bi bi-download"
        viewBox="0 0 16 16"
        style="margin-right:5px"
      >
        <path
          d="M.5 9.9a.5.5 0 0 1 .5.5v2.5a1 1 0 0 0 1 1h12a1 1 0 0 0 1-1v-2.5a.5.5 0 0 1 1 0v2.5a2 2 0 0 1-2 2H2a2 2 0 0 1-2-2v-2.5a.5.5 0 0 1 .5-.5z"
        />
        <path
          d="M7.646 11.854a.5.5 0 0 0 .708 0l3-3a.5.5 0 0 0-.708-.708L8.5 10.293V1.5a.5.5 0 0 0-1 0v8.793L5.354 8.146a.5.5 0 1 0-.708.708l3 3z"
        />
      </svg>
      Install for iOS
    </v-btn>
    <b-modal id="modal-1" title="Install app on iOS">
    <p class="my-4">
        1. Tap the 'Share' button 
        <img src="../assets/ios-share-icon-15.jpg" id="ios-share-icon">
        <br>
        2. Scroll down and tap 'Add to Home Screen'
        <br>
        3. Tap add
        </p>
  </b-modal>
  </div>
</template>

<script>
export default {

}
</script>

<style>
    #ios-share-icon{
        width: 6%;
        height: 10%;
        padding-bottom: 6px;
    }
</style>