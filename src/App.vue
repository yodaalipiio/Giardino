<template>
  <MDBContainer fluid class="background-whole">
    <MDBNavbar expand="lg" style="background: #385424;" container>
      <MDBNavbarBrand ><img src="../../logo2.png" loading="lazy" height="200" width="200"></MDBNavbarBrand>
    <!-- Toggle button -->
    <MDBNavbarToggler class="text-white"
      target="#navbarRightAlignExample"
      @click="collapse5 = !collapse5"
    ></MDBNavbarToggler>
    <!-- Collapsible wrapper -->
    <MDBCollapse v-model="collapse5" id="navbarRightAlignExample">

      <MDBNavbarNav right class="mb-3 mb-lg-0">
        <!-- Right links -->
       <MDBNavbarItem active>
          <form method="get" action="/search">
              <div class="field has-addons">
                <div class="control">
                  <input type="text" class="input" placeholder="Search for products here" name="query">
                </div>

                <div class="control">
                  <MDBBtn color="warning">
                      <span class="icon">
                      <i class="fas fa-search"></i>
                      </span>
                  </MDBBtn>
                </div>
              </div>
            </form>
        </MDBNavbarItem>
        <br>
        <MDBNavbarItem active>
          <router-link to="/" ><MDBBtn color="#385424;" class="text-white">Home</MDBBtn></router-link>
        </MDBNavbarItem>
        <br>
        <MDBNavbarItem  active>
          <router-link to="/about" ><MDBBtn color="#385424;" class="text-white">About</MDBBtn></router-link>
        </MDBNavbarItem>
        <br>
        <MDBNavbarItem  active>
          <router-link to="/contact-us" ><MDBBtn color="#385424;" class="text-white">Contact Us</MDBBtn></router-link>
        </MDBNavbarItem>
        <br>
         <MDBNavbarItem  active>
          <router-link to="/store"><MDBBtn color="#385424;" class="text-white">Store</MDBBtn></router-link>
        </MDBNavbarItem>
        <br>
         <MDBNavbarItem  active >
         <template v-if="$store.state.isAuthenticated">
               <MDBBtn color="warning"><router-link to="/my-account" class="text-white">My account</router-link></MDBBtn> 
              </template>
          
              <template v-else>
                <MDBBtn color="warning"> <router-link to="/login" class="text-white">Log in</router-link></MDBBtn>
              </template>
          </MDBNavbarItem>
          <br>
          <MDBNavbarItem active>
               <router-link to="/cart"><MDBBtn color="warning"> 
                <span class="badge badge-pill bg-danger">{{ cartTotalLength }}</span>
                <span class="icon text-white"><i class="fas fa-shopping-cart"></i></span>
              </MDBBtn></router-link> 
          </MDBNavbarItem>
          <br>
        
        
        
        <!-- Right links -->
      </MDBNavbarNav>
    </MDBCollapse>
    <!-- Collapsible wrapper -->
  </MDBNavbar>

    <div class="is-loading-bar has-text-centered" v-bind:class="{'is-loading': $store.state.isLoading }">
      <div class="lds-dual-ring"></div>
    </div>

    <section class="section">
      <router-view/>
    </section>

   <MDBFooter :text="['center', 'lg-start']">
    <!-- Copyright -->
    <div class="text-center p-3 text-white" style="background-color:#385424;">
      © 2021 Copyright
    </div>
    <!-- Copyright -->
  </MDBFooter>
  </MDBContainer>
</template>

<script>
import axios from 'axios'
import {
    MDBContainer,
    MDBNavbar,
    MDBNavbarToggler,
    MDBNavbarBrand,
    MDBNavbarNav,
    MDBNavbarItem,
    MDBCollapse,
    MDBDropdown,
    MDBDropdownToggle,
    MDBDropdownMenu,
    MDBDropdownItem,
    MDBBtn,
    MDBBtnGroup,
    MDBFooter,
  } from 'mdb-vue-ui-kit';
  import { ref } from 'vue';

export default {
  data() {
    return {
      showMobileMenu: false,
      cart: {
        items: []
      }
    }
  },
  beforeCreate() {
    this.$store.commit('initializeStore')

    const token = this.$store.state.token

    if (token) {
        axios.defaults.headers.common['Authorization'] = "Token " + token
    } else {
        axios.defaults.headers.common['Authorization'] = ""
    }
  },
  mounted() {
    this.cart = this.$store.state.cart
  },
  computed: {
      cartTotalLength() {
          let totalLength = 0

          for (let i = 0; i < this.cart.items.length; i++) {
              totalLength += this.cart.items[i].quantity
          }

          return totalLength
      }
  },
  components: {
      MDBContainer,
      MDBNavbar,
      MDBNavbarToggler,
      MDBNavbarBrand,
      MDBNavbarNav,
      MDBNavbarItem,
      MDBCollapse,
      MDBDropdown,
      MDBDropdownToggle,
      MDBDropdownMenu,
      MDBDropdownItem,
      MDBBtn,
      MDBBtnGroup,
      MDBFooter,
    },
    setup() {
      const collapse5 = ref(false);
      const dropdown8 = ref(false);

      return {
        collapse5,
        dropdown8
      }
    }
}
</script>

<style lang="scss">
@import '../node_modules/bulma';

.lds-dual-ring {
  display: inline-block;
  width: 80px;
  height: 80px;
}
.lds-dual-ring:after {
  content: " ";
  display: block;
  width: 64px;
  height: 64px;
  margin: 8px;
  border-radius: 50%;
  border: 6px solid #ccc;
  border-color: #ccc transparent #ccc transparent;
  animation: lds-dual-ring 1.2s linear infinite;
}
@keyframes lds-dual-ring {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}

.is-loading-bar {
  height: 0;
  overflow: hidden;

  -webkit-transition: all 0.3s;
  transition: all 0.3s;

  &.is-loading {
    height: 80px;
  }
}
.background-whole{
background-image: url('../../dot-grid.png'); 
background-repeat: repeat;
}

</style>
