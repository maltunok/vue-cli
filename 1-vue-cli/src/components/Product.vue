<template>
    <div class="product">
        <strong>{{product.title}}</strong>
        <p>{{product.description}}</p>
        <strong>Price:{{product.price}} | Count: {{product.count}}</strong>
        <br>
        <br>
        <button @click="addcart(product)">sepete ekle</button>
     
    </div>
</template>
<script>
export default {
    props: ["product"],
    methods:{
        addcart(product){
         this.$emit("addcart", product)
        }
    }
}
</script>
<style>
.product {
    border:2px dashed #666; 
    padding: 10px 10px;
    width:300px;
    margin-bottom: 5px;
}   
.product:hover{
    border:2px solid #666;
    transition: all .5;
}

</style>