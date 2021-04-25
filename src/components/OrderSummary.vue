<template>
    <MDBContainer fluid>
        <div class="d-flex flex-wrap">
         <h3 class="fs-4">Order #{{ order.id }}</h3>
        <MDBTable>
    <thead>
      <tr>
        <th scope="col">Product</th>
        <th scope="col">Price</th>
        <th scope="col">Quantity</th>
        <th scope="col">Total</th>
      </tr>
    </thead>
    <tbody>
      <tr
        v-for="item in order.items"
        v-bind:key="item.product.id"
                >
        <td>{{ item.product.name }}</td>
        <td>₱{{ item.product.price }}</td>
        <td>{{ item.quantity }}</td>
        <td>₱{{ getItemTotal(item).toFixed(2) }}</td>
      </tr>
    </tbody>
  </MDBTable>
  </div>
    </MDBContainer>
</template>

<script>
import { MDBTable, MDBContainer } from 'mdb-vue-ui-kit';
export default {
    name: 'OrderSummary',
    props: {
        order: Object
    },
    methods: {
        getItemTotal(item) {
            return item.quantity * item.product.price
        },
        orderTotalLength(order) {
            return order.items.reduce((acc, curVal) => {
                return acc += curVal.quantity
            }, 0)
        },
    }, 
    components: {
      MDBTable, MDBContainer
    },
}
</script>