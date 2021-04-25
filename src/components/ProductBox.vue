<template>
      <MDBCard>
        <MDBCardImg top v-bind:src="product.get_thumbnail" style="width:15rem; margin-left:5px; padding-left:5px;"/>
        <MDBCardBody>
          <MDBCardTitle><h4>{{ product.name }}</h4></MDBCardTitle>
          <MDBCardText>
            <p  class="text-end">₱{{ product.price }}</p>
            <router-link v-bind:to="product.get_absolute_url" class="button is-dark mt-4">View details</router-link>
          </MDBCardText>
        </MDBCardBody>
      </MDBCard>
</template>

<script>
import { 
MDBCard, 
MDBCardBody, 
MDBCardTitle, 
MDBCardText, 
MDBCardImg,
MDBRow,
      MDBCol,
      MDBCardGroup } from "mdb-vue-ui-kit";

export default {
    name: 'ProductBox',
    props: {
        product: Object
    },

    components: {
      MDBCard,
      MDBCardBody,
      MDBCardTitle,
      MDBCardText,
      MDBCardImg,
      MDBRow,
      MDBCol,
      MDBCardGroup
    }
}
</script>

<style scoped>
  
</style>