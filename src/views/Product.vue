<template>
<MDBContainer fluid>
    <div class="d-flex flex-wrap justify-content-center" >
    <MDBRow :cols="['1','md-2']" class="g-4">
    <MDBCol >
      <MDBCard>
        <MDBCardImg class=" rounded shadow-3 mb-3 " v-bind:src="product.get_image"
                   />
        <MDBCardBody>
          <MDBCardTitle><h1 class="title">{{ product.name }}</h1></MDBCardTitle>
          <MDBCardText>
            <p class="fs-4">{{product.description}}</p>
          </MDBCardText>
        </MDBCardBody>
      </MDBCard>
    </MDBCol>
    <MDBCol>
      <MDBCard>
        <MDBCardBody>
          <MDBCardTitle>Information:</MDBCardTitle>
          <MDBCardText>
           <h2 class="subtitle">Information</h2>

                <p><strong>Price: </strong>₱{{ product.price }}</p>

                <div class="field has-addons mt-6">
                    <div class="control">
                        <input type="number" class="input" min="1" v-model="quantity">
                    </div>

                    <div class="control">
                        <a class="button is-warning" @click="addToCart()">Add to cart</a>
                    </div>
                </div>
          </MDBCardText>
        </MDBCardBody>
      </MDBCard>
    </MDBCol>
    </MDBRow>
  </div>
</MDBContainer>
</template>

<script>
import axios from 'axios'
import { toast } from 'bulma-toast'
import { MDBRow, MDBCol, MDBCard, MDBCardBody, MDBCardTitle, MDBCardText, MDBCardImg } from "mdb-vue-ui-kit";

export default {
    name: 'Product',
    data() {
        return {
            product: {},
            quantity: 1
        }
    },
    mounted() {
        this.getProduct() 
    },
    methods: {
        async getProduct() {
            this.$store.commit('setIsLoading', true)

            const category_slug = this.$route.params.category_slug
            const product_slug = this.$route.params.product_slug

            await axios
                .get(`/api/v1/products/${category_slug}/${product_slug}`)
                .then(response => {
                    this.product = response.data

                    document.title = this.product.name + ' | Giardino Pots'
                })
                .catch(error => {
                    console.log(error)
                })
            
            this.$store.commit('setIsLoading', false)
        },
        addToCart() {
            if (isNaN(this.quantity) || this.quantity < 1) {
                this.quantity = 1
            }

            const item = {
                product: this.product,
                quantity: this.quantity
            }

            this.$store.commit('addToCart', item)

            toast({
                message: 'The product was added to the cart',
                type: 'is-success',
                dismissible: true,
                pauseOnHover: true,
                duration: 2000,
                position: 'bottom-right',
            })
        }
    },
    components: {
      MDBRow,
      MDBCol,
      MDBCard,
      MDBCardBody,
      MDBCardTitle,
      MDBCardText,
      MDBCardImg
    }
}
</script>