<template>
<b-container>
          <table class="table table-striped">
            <thead>
            <tr>
              <th>Name</th>
              <th>Price</th>
              <th>SKU</th>
              <th>Edit</th>
              <th>Delete</th>
            </tr>
            </thead>
            <tbody>
            <tr v-for="product in products" :key="product.sku" :product="product">
              <td>{{product.name}}</td>
              <td>${{product.price}}</td>
              <td>{{product.sku}}</td>
              <td><router-link :to="'/admin/edit/'+product.sku"><i class="far fa-edit"></i></router-link></td>
              <td><a @click="deleteProduct(product.sku)"><i class="far fa-trash-alt"></i></a></td>
            </tr>
            </tbody>
          </table>
        </b-container>
</template>


<script>
const apiURL = 'https://shoppingcartapi-icwz30bz4.now.sh';

import axios from 'axios';
export default {
    name: 'AdminProductList',
    data() {
        return {
            products: {}
        }
    },

    created() {
        this.fetchData()
    },

    methods: {
        deleteProduct(sku) {
          console.log("sku to delete",sku)
          axios.delete(`${apiURL}/product/${sku}`)
            .then(this.fetchData())
            .catch((err) => {
                alert("Error Deleting");
                console.log(err);
            });
        },
        fetchData() {
            axios.get(`${apiURL}/products`)
                .then((resp) => {
                    this.products = resp.data;
                    console.log(resp);
                })
                .catch((err) => {
                  this.products = {};
                  alert("Products Not Found");
                    console.log(err);
                })
        },
    }
}
</script>
