<template>
    <MDBContainer fluid>
         <div class="d-flex flex-column mb-3" style="height:37vw">
            <div class="p-2"><h1 class="title">Thank you for ordering!</h1></div>
            <div class="p-2"><p>Your order will be processed within 48 hours. Please check your email/contact number for the shipping info</p></div>
          
        </div>
    </MDBContainer>
</template>

<script>
export default {
    name: 'Success',
    mounted() {
        document.title = 'Success | Giardino Pots'
    },
}
</script>