<template>
<div class="cart-item-card">
    <div class="header">
        <!-- this is the product item cart -->
        <h4>{{product.name}}</h4>
        <h4>In Cart: {{product.quantity}}</h4>
        <h4>Total Cost: {{item_cost.toFixed(2)}}</h4>
    </div>
    <p>{{description}}</p>
    </div>
</template>

<script>
export default {
    name: 'cartitemcard',
    props : ['product'],
    computed:{
        description(){
            return this.product.description.substring(0, 100)
        },
        item_cost(){
            return this.product.price * this.product.quantity
        },
    }
}
</script>

<style lang="scss">
    .cart-item-card{
        width: 90%;
        margin: 5%;
        background-color: white;
        padding: 10px;
        box-shadow: 0 0 5px gray;
        text-align: left;
        border-radius: 5px;

        .header{
            display: flex;
            justify-content: space-around;
        }
    }
</style>]