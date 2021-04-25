<template>
    <MDBContainer fluid>
         <div
      class="p-5 text-center bg-image"
      style="
        background-image: url('https://images.unsplash.com/photo-1527341944416-23e85b614715?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=1050&q=80');
        height: 315px;
      "
    >
      <div class="mask" style="background-color: rgba(0, 0, 0, 0.6);">
        <div class="d-flex justify-content-center align-items-center h-100">
          <div class="text-white" style="padding:50px; margin:50px;">
            <h1 class="mb-3">Contact Us!</h1>
            <h4 class="mb-3">Follow us on:</h4>
              <MDBBtn color="primary" style="width:8rem; margin-bottom:5px;" > <a href="https://www.facebook.com/GiardinoPots" target="_blank"> <span class="icon text-white"><i class="fab fa-facebook-square"></i> Facebook</span></a> </MDBBtn>
               
               <MDBBtn style=" background-color:#ff6f3d; width:8rem; margin-bottom:5px;"> <a href="https://shopee.ph/micccchhhhh?smtt=0.0.9&fbclid=IwAR1N6QT1AiWozSXkHKyc5X3CqVvon9NGInnVm-W54LkPgaTinLCDzTztFCc" target="_blank"><span class="icon text-white"><i class="fas fa-shopping-bag"></i>  Shopee</span></a> </MDBBtn> 
          </div>
        </div>
      </div>
    </div>
    <br>
    <div class="d-flex justify-content-center">
        <div class="row">
            <div class="col-sm-4">
        <iframe src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d2296.1500065128944!2d121.22598102051651!3d14.56207550568814!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x0%3A0xcb7ac55b59577c93!2sCarissa%20Homes%20East%202%20Brgy.%20Dalig%20Teresa%2C%20Rizal!5e0!3m2!1sen!2sph!4v1619375976403!5m2!1sen!2sph" width="300" height="300" style="border:0;" allowfullscreen="" loading="lazy"></iframe>
        </div>
        
        <div class="col-sm-8">
            <MDBCard style="margin-left:6rem;">
            <MDBCardBody>
                <MDBCardTitle><h1 class="display-4 text-start">location:</h1></MDBCardTitle>
                <MDBCardText>
                    71 La Natividad Road, Pantay, Dalig, Teresa, Rizal

                </MDBCardText>
                </MDBCardBody>
            </MDBCard>
            <MDBCard style="margin-left:6rem;">
            <MDBCardBody>
                <MDBCardTitle><h1 class="display-4 text-start">contact no.:</h1></MDBCardTitle>
                <MDBCardText>
                   <i class="fas fa-phone-alt"></i> 09275581151

                </MDBCardText>
                </MDBCardBody>
            </MDBCard>
        </div>
        </div>
        
    </div>
    </MDBContainer>
</template>
<script>
import { MDBBtn, MDBNavbar, MDBNavbarToggler, MDBNavbarNav, MDBNavbarItem, MDBCard, MDBCardBody, MDBCardTitle, MDBCardText } from 'mdb-vue-ui-kit';
export default {
    name: 'Contact',
    mounted() {
         document.title = 'Contact Us | Giardino Pots'
    },
    components: {
      MDBBtn,
      MDBNavbar,
      MDBNavbarToggler,
      MDBNavbarNav,
      MDBNavbarItem,
      MDBCard, 
      MDBCardBody, 
      MDBCardTitle, 
      MDBCardText,
    },
}
</script>