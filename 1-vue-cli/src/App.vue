<template>
<div class="container">
  <div class="cart">
    <h3>sepet</h3>
    <ul>
      <li v-for="item in cartItems" :key="item.id">{{item.title}}</li>
    </ul>
    <p v-if ="cartItems.length==0">Sepetiniz boştur...Alışverişe başlayabilirsiniz...</p>
  </div>
  <hr>
  <!--<myComp></myComp>-->
  <Product @addcart="cartItems.push($event)" :product ="product" v-for="product in productList" :key="product.id"/>

</div>
</template>
<script>
//import MainContainer from "@/components/MainContainer.vue"
import Product from "@/components/Product.vue"
export default{
components:{
  //myComp: MainContainer
  Product
},
data(){
  return{
    productList: [
      {
        id:1,
        title:"McBookPro",
        price:100,
        count:50,
        description:"ssss"
      },
      {
        id:2,
        title:"iPhone",
        price:50,
        count:100,
        description:"dddd"
      },
      {
        id:3,
        title:"keyboard",
        price:10,
        count:1000,
        description:"ffff"
      }
    ],
    cartItems :[]
  }
}
}
</script>
<style>
.container{
display: flex;
justify-content: center;
align-items: center;
flex-direction: column;
}
.cart{
  margin-bottom: 50px;
}
</style>