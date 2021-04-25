<template>
    <div class="container">
       <MDBRow>
            <div class="col-md-12">
                <h1 class="title">My account</h1>
                <button @click="logout()" class="button is-danger float-end justify-content-end">Log out</button>
            </div>
            <hr>

            <div class="d-flex flex-wrap col-md-12">
                <h2 class="subtitle">My orders</h2>
            <div class="row">
                <OrderSummary
                    v-for="order in orders"
                    v-bind:key="order.id"
                    v-bind:order="order" />
            </div>
            </div>
            
        </MDBRow>
    </div>
</template>

<script>
import axios from 'axios'

import OrderSummary from '@/components/OrderSummary.vue'

export default {
    name: 'MyAccount',
    components: {
        OrderSummary
    },
    data() {
        return {
            orders: []
        }
    },
    mounted() {
        document.title = 'My account | Giardino Pots'

        this.getMyOrders()
    },
    methods: {
        logout() {
            axios.defaults.headers.common["Authorization"] = ""

            localStorage.removeItem("token")
            localStorage.removeItem("username")
            localStorage.removeItem("userid")

            this.$store.commit('removeToken')

            this.$router.push('/')
        },
        async getMyOrders() {
            this.$store.commit('setIsLoading', true)

            await axios
                .get('/api/v1/orders/')
                .then(response => {
                    this.orders = response.data
                })
                .catch(error => {
                    console.log(error)
                })

            this.$store.commit('setIsLoading', false)
        }
    },
    
}
</script>