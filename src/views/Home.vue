<template>
<header>
  <MDBContainer fluid>
    <!-- Background image -->
    <div class="p-5 bg-image" style=" background-image: url('https://images.unsplash.com/photo-1525247862234-30193931fdf7?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=1248&q=80'); height:600px">
      <div class="mask" style="background-color: rgba(0, 0, 0, 0.6); padding-left:5rem;">
        <div class="d-flex justify-content-start align-items-center h-100">
          <div class="text-white" style="margin-right:5rem;">
            <h1 class="mb-3">Welcome to Giardino Pots!</h1>
            <h4 class="mb-3">Art N Plant in a pot</h4>
          </div>
        </div>
      </div>
    </div>
    <!-- Background image -->
<br>
<div class="d-flex justify-content-center ">
  
  <MDBCard class= "w-100" style="background:#3e503c;">
    <MDBCardBody>
      <MDBCardTitle><h1 class= "shadow-5 display-5 text-center" style="color: #f3ecdb">Latest Products</h1></MDBCardTitle>
    </MDBCardBody>
  </MDBCard>
</div>

<br>
  <div class="d-flex flex-wrap justify-content-center">
      <ProductBox
        v-for="product in latestProducts"
        v-bind:key="product.id"
        v-bind:product="product" />
  </div>
  
  

    </MDBContainer>
  </header>
</template>

<script>
import axios from 'axios'
import { MDBRow, MDBCard, MDBCardBody, MDBCardTitle, MDBCardText, MDBBtn, MDBCol, MDBContainer } from "mdb-vue-ui-kit";
import ProductBox from '@/components/ProductBox'

export default {
  name: 'Home',
  data() {
    return {
      latestProducts: []
    }
  },
  components: {
    ProductBox,
    MDBCard,
    MDBCardBody,
    MDBCardTitle,
    MDBCardText,
    MDBBtn,
    MDBCol,
    MDBContainer,
    MDBRow
  },
  mounted() {
    this.getLatestProducts()

    document.title = 'Home | Giardino Pots'
  },
  methods: {
    async getLatestProducts() {
      this.$store.commit('setIsLoading', true)

      await axios
        .get('/api/v1/latest-products/')
        .then(response => {
          this.latestProducts = response.data
        })
        .catch(error => {
          console.log(error)
        })

      this.$store.commit('setIsLoading', false)
    }
  },
 
}
</script>