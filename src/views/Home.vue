<template>
  <div class="home">
    <productdescriptiondrawer
    :product = "product"
    :active="active.product_drawer"
    @close-product-drawer = "closeProductDrawer"/>
    
    <div class="product-cards-container">
      <productsummarycard
      v-for="product in items"
      :key="product.id"
      :product="product"
      @view-product="viewProduct($event)"/>
      
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import items from '../data/item.js'
import productsummarycard from '../components/products/ProductSummaryCard.vue'
import productdescriptiondrawer from '../components/products/ProductDescriptionDrawer.vue'

export default {
  name: 'Home',
  components: {
    productsummarycard,
    productdescriptiondrawer,
    
  },
  data(){
    return{
      items:items,
      product:null,
      active :{
        product_drawer : false
      }
    }
  },
  methods:{
    viewProduct(product){
      this.active.product_drawer = true
      this.product = product

      // console.log(this.product)
    },
    closeProductDrawer(){
      this.active.product_drawer = false
    }
  }
}
</script>
<style lang="scss">
  .product-cards-container{
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
  }
</style>