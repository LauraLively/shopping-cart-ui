<template>
  <div class="card p-3">
    <div class="text-center">
      <router-link :to="`/product/${product.sku}`"><img class="img-fluid" :src="product.image" width="300rem" :product="product"></router-link>
      <div class="card-body">
        <h4 class="card-title">{{ product.name }} </h4>
        <h5>${{product.price}} </h5>
        <div class="product__action">
          <b-button>Add to Cart</b-button>
        </div>      
      </div>
    </div>
  </div>
</template>

<script>
const apiURL = 'https://shoppingcartapi-icwz30bz4.now.sh';
export default {
  name: 'productCard',
  props: {
    // this component expects a prop of type object
    product: {
      type: Object,
      required: true
    }
  },
}
</script>