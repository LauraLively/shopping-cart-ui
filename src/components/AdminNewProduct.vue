<template>
        <b-container>
        <b-form id="newProduct" @submit="onSubmit" class="admin-form-right">
            <h3>Add a Product</h3>
            <b-form-input id="name" v-model="product.name" type="text" required placeholder="Name of Product" />
            <b-form-input id="sku" v-model="product.sku" type="text" required placeholder="SKU of Product" />
            <b-form-input id="price" v-model="product.price" type="number" step=".01" required placeholder="Price" />
            <b-form-input id="image" v-model="product.image" type="text" required placeholder="URL of Product" />
            <b-form-textarea id="desc" v-model="product.description" type="text" required placeholder="Description" />
            <b-button type="submit" variant="info">Submit</b-button>
        </b-form>
        
    </b-container>
</template>

<script>
const apiURL = 'http://localhost:3000';
import axios from 'axios';
export default {
    name: 'Product',
    data() {
        return {
            product: {
            name: '',
            sku: '',
            price: '',
            image: '',
            description: ''
            }
        }
    },

    // created() {
    //     this.fetchData()
    // },

    // watch: {
    //     '$route': 'fetchData'
    // },

    methods: {
        onSubmit(e) {
            e.preventDefault();
            console.log("product", this.$data.product);
            axios.post(`${apiURL}/product`, this.$data.product)
                .then((resp) => {
                    this.product = resp.data;
                    console.log(resp)
                    this.$router.push('/admin');
                })
                .catch((err) => {
                  alert("Product Not Found");
                    console.log(err)
                })
        }
    },
}
</script>
