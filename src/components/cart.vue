<template>
<div>
    <h1>Cart</h1>
    <div v-if='cart.length > 0'>
        <h1>Your Cart</h1>
    <template>
        <fieldset v-for='product in cart'>
            <image :src='product.image'
            <h4>{{product.name}}</h4>
            <input type='number' min= 1 :max='product.quantity'/>
            <h5>{{product.price}}</h5>
            <!-- <submit value='Remove' @submit='removeFromCart' /> -->
        </fieldset>
    </template>
    </div>
    <div v-else><h1>Your Cart Is Empty</h1></div>
    <br />
    <h5 v-model='filterPrice'></h5>
    <h5>Shipping: Free for a limited time!</h5>
    <h2>Total: </h2>
</div>
</template>
<script>
const apiURL = 'http://localhost:3000';
import axios from 'axios';
export default {
    data() {
        return {
            cart: [
                    {
                id:"56461",
                name:"lilly",
                quantity: 10,
                price: 30.10
                }, {
                id:"1253",
                name:"wild",
                quantity: 7,
                price: 31.10
                }
                ]
            }
        },
    // methods: {
    // }
    computed: {
        // filterPrice() {
        //     let result = [];
        //     cart.forEach(product => {
        //         product.filter(price)
        //     });
        //}
        filterPrice() { cart.filter(product => {
            product.price
        })
        }
        // getSubtotal = () => {
        //     filterPrice.forEach(product => 
        //     )}
        }
    }
</script>