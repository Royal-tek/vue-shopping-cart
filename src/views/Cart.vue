<template>
    <div>
        <h1>Your Cart</h1>
        <cartitemcard v-for="product in items" :key="product.id" :product="product" />
        <cartPaymentSummaryCard />
    </div>
</template>

<script>
import cartitemcard from '../components/cart/CartItemCard.vue'
import cartPaymentSummaryCard from '../components/cart/cartPaymentSummaryCard.vue'

export default {
    components:{
        cartitemcard, cartPaymentSummaryCard
    },
    computed :{
        items(){
            return this.$store.getters.cartItems
        }
    }
}
</script>