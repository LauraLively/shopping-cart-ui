<template>
        <b-container>
<!-- @submit handles any form of submission. -->
<!-- .prevent keeps the event from bubbling around and doing anything else. -->
        <b-form @submit="onSubmit" class="admin-form-right">
            <h3>Edit Product</h3>
            <b-form-input v-model="product.name" type="text" required placeholder="Name of Product" />
            <b-form-input v-model="product.sku" type="text" readonly placeholder="SKU of Product" />
            <b-form-input v-model="product.price" type="number" step=".01" required placeholder="Price" />
            <b-form-input v-model="product.image" type="text" required placeholder="URL of Product" />
            <b-form-textarea v-model="product.description" type="text" required placeholder="Description" />
            <b-button type="submit" variant="info">Submit</b-button>
            <!-- <b-button type="reset" variant="secondary">Reset</b-button> -->
        </b-form>
    </b-container>
</template>
<script>
const apiURL = 'https://shoppingcartapi-icwz30bz4.now.sh';
import axios from 'axios';
export default {
    name: 'AdminEditProduct',
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
            console.log("Fetch data", sku);
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
        },
        onSubmit(e) {
            e.preventDefault();  
            let sku = this.$route.params.sku;          
            console.log("product", this.$data.product);
            axios.put(`${apiURL}/product/${sku}`, this.$data.product)
                .then((resp) => {
                    console.log(resp)
                    this.$router.push('/admin');
                })
                .catch((err) => {
                  alert("Product Not Updated");
                    console.log(err)
                })
        }

    }
}
</script>
