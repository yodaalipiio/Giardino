<template>
  <MDBContainer>
     <!-- Background image -->
     <div
      class="p-5 text-center bg-image"
      style="
        background-image: url('https://images.unsplash.com/photo-1466517158279-36780cbb0b5a?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=1050&q=80');
        height: 400px;
      "
    >
      <div class="mask" style="background-color: rgba(0, 0, 0, 0.6);">
        <div class="d-flex justify-content-start align-items-center h-100">
          <div class="text-white" style="margin:5rem;">
            <h1 class="mb-3">The story...</h1>
            <h4 class="mb-3">The pandemic, the plantita and the passion...</h4>
          </div>
        </div>
      </div>
    </div>
    <!-- Background image -->
    <hr>
    <h1 class="title">Where it all began</h1>
    <p class="lh-4">
    Giardino Pots is the brainchild of a humble university student from Teresa, Rizal. Having an adventurous spirit, she was willing to take on any form of challenge during these trying times. Being in a family of four with only her mother working, she sought out to try different businesses to overcome the hardships that CoVID - 19 has brought upon all walks of life.
  </p>
  <h1 class="title">How are they made?</h1>
    <p class="lh-4">
    With a simple idea of producing pots of excellent quality to be vessels for her prized plants, Giardino Pots are hand-made thus making each pot unique and special. 
  </p>
  <h1 class="title">Arts N Plants in a pot</h1>
    <p class="lh-4">
    Art has numerous forms. From paintings to sculptures to pottery. Art is appreciated no matter what shape or for. Giardino Pots are for those seeking aesthetics combined with the beauty of nature itself.
  </p>
  </MDBContainer>
</template>

<script>
import { MDBBtn, MDBNavbar, MDBNavbarToggler, MDBNavbarNav, MDBNavbarItem } from 'mdb-vue-ui-kit';
export default {
  
  name: 'About',
  mounted(){
    document.title = 'About | Giardino Pots'
  },
  components: {
      MDBBtn,
      MDBNavbar,
      MDBNavbarToggler,
      MDBNavbarNav,
      MDBNavbarItem
    },
}
</script>