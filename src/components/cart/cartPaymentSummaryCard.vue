<template>
    <div class="cart-item-card">
        <h3>Cart Total: ${{cart_total.toFixed(2)}}</h3>
        <button class="view-product-button">Pay by credit card</button>
    </div>
</template>

<script>
export default {
    name:'cartpaymentsummarycard',
    computed:{
        cart_total(){
            return this.$store.getters.cart_total
        }
    }
}
</script>