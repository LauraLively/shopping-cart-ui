<template>
<b-container>
<div id="Product">
    <div class="product">
        <div class="product-image">
            <img v-bind:src="product.image"/>
        </div>
        <div class="product-info">
            <h1>{{ product.name }}</h1>
            <h2>${{ product.price }} </h2>
            <p>{{ product.description }} </p>
            <b-button>Add to Cart</b-button>
            <b-button>Remove from Cart</b-button>
        </div>
    </div>
</div>
</b-container>
</template>

<script>
const apiURL = 'https://shoppingcartapi-icwz30bz4.now.sh';
import axios from 'axios';
export default {
    name: 'Product',
    data() {
        return {
            product: {}
        }
    },

    created() {
        this.fetchData()
    },

    watch: {
        '$route': 'fetchData'
    },

    methods: {
        fetchData() {
            let sku = this.$route.params.sku;
            axios.get(`${apiURL}/product/${sku}`)
                .then((resp) => {
                    this.product = resp.data;
                    console.log(resp)
                })
                .catch((err) => {
                  this.product = {};
                  alert("Product Not Found");
                    console.log(err)
                })

        }
    }
}
</script>
