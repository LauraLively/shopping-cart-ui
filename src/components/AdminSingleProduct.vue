<template>
    <td>{{product.name}}</td>
    <td>${{product.price}}</td>
    <td>{{product.sku}}</td>
    <td><router-link :to="'/admin/edit/'+product.sku"><i class="far fa-edit"></i></router-link></td>
    <td><a v-on:click="deleteProduct(product.sku)"><i class="far fa-trash-alt"></i></a></td>
</template>

<script>
export default {
 name: 'AdminSingleProduct',
    
}
</script>
