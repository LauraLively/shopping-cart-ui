<template>
<b-container>
    <h1>Products</h1>
    <div class="card-columns">
        <product-card v-for="product in products" :key="product.sku" :product="product"></product-card>
    </div>
</b-container>
</template>

<script>
const apiURL = 'https://shoppingcartapi-icwz30bz4.now.sh';
import productCard from '@/components/ProductCard';
import axios from 'axios';
export default {
    name: 'Products',
      components: {
        'product-card': productCard
  },

    data() {
        return {
            products: {}
        }
    },

    created() {
        this.fetchData()
    },

    methods: {
        fetchData() {
            axios.get(`${apiURL}/products`)
                .then((resp) => {
                    this.products = resp.data;
                    console.log(resp)
                })
                .catch((err) => {
                  this.products = {};
                  alert("Products Not Found");
                    console.log(err)
                })

        }
    }
}
</script>
