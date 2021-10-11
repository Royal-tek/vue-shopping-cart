<template>
    <div class="drawer-background" :class="{show : active}" @click="$emit('close-product-drawer')"/>
    <div class="drawer" :class="{show:active}">
        <div class="close-drawer" @click="$emit('close-product-drawer')">
            X
        </div>

        <div class="product-detail" v-if="product">
            <h3 class="text-center">{{product.name}}</h3>
            <p class="description">{{product.description}}</p>
            <h3 class="text-center">{{product.price.toFixed(2)}}</h3>

        <div class="cart-total" v-if="product_total">
            <h3>In cart</h3>
            <h4>{{product_total}}</h4>
        </div>

        <div class="button-container">
            <button class="remove" @click="removeFromCart()">Remove</button>
            <button class="remove" @click="addToCart()">Add</button>
        </div>

        </div>

    </div>
    
</template>
<script>
export default {
    name:'productdescriptiondrawer',
    props : ['product', 'active'],
    methods :{
        addToCart(){
            this.$store.commit('addToCart', this.product)
        },
        removeFromCart(){
            this.$store.commit('removeFromCart', this.product)
        }
    },
    computed:{
        product_total(){
            return this.$store.getters.productQuantity(this.product)
        },
    },
    
}
</script>

<style lang="scss">
.drawer-background{
    width: 100%;
    height: 100vh;
    background-color: rgba(124, 124, 124, 0.55);
    z-index: 100;
    position: fixed;
    left: 0;
    transition: 2s;
    top: 0;
    transition: 2s;
    display: none;

    &.show{
        display: block;
    }
}
.drawer{
    background-color: white;
    width: 95vw;
    position: fixed;
    left: -105vw;
    height: 100vh;
    top: 0;
    z-index: 101;
    transition: left 1s;
    padding: 15px;
    overflow-y: scroll;

    &.show{
        left: 0;
    }
    .close-drawer{
        padding: 5px;
        float: right;
        border: 2px solid gray;
        cursor: pointer;
        border-radius: 5px;
        right: 10px;
        color: gray;
        font-size: 1.5rem;

        &:hover{
            background-color: lightgray;
            transition: .5s;
        }
    }
}
.product-detail{
    display: flex;
    justify-content: center;
    flex-direction: column;

    p.description{
        padding: 20px;
        line-height: 1.5rem;
    }
    
    .button-container{
        button{
            width: 150px;
            border: none;
            padding: 10px;
            border-radius: 5px;
            cursor: pointer;
            margin: 0 5px 50px 5px;
        }
    }
}
@media (min-width: 450px){
    .drawer{
        width: 450px;
    }
}
.text-center{
    text-align: center;
}
</style>