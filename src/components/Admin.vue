<template>
<div>
    <h1>Admin</h1>
    <b-container>
        <div class="admin-new">
            <div class="container">
                    <ul class="admin-menu">
                        <li>
                            <router-link to="/admin">View Products</router-link>
                        </li>
                        <li>
                            <router-link to="/admin/new">New Product</router-link>
                        </li>
                    </ul>
                <router-view></router-view>
            </div>
        </div>
    </b-container>
</div>
</template>

<script>

export default {

    data() {
        return {
        }
    },
    methods: {
        onSubmit(evt) {
            evt.preventDefault()
            alert(JSON.stringify(this.form))
        },
        onReset(evt) {
            evt.preventDefault()
            /* Reset our form values */
            this.form.name = ''
            this.form.SKU = ''
            this.form.price = ''
            this.form.description = ''
            /* Trick to reset/clear native browser form validation state */
            this.show = false
            this.$nextTick(() => {
                this.show = true
            })
        }
    }
}
</script>

<style>
.admin-form-right input,
textarea,
button {
    margin-bottom: 1em;
}
.admin-form-right{
    margin-left: 5rem;
    margin-right: 5rem;
}
.admin-menu li {
    list-style-type: none;
}
.admin-menu {
    padding-inline-start: 0px !important;
    margin-left: 5rem;
    margin-right: 5rem;

}

.admin-menu a {
    display: block;
    background:#17a2b8 !important;
    border: 1px solid #71AEB7;
    color: #fff;
    padding: 10px 15px;
    font-weight: bold;
    text-transform: uppercase;
    font-size: 0.9em;
    transform: scaleX(1);
    transition: transform 200ms ease-in;
    text-align: center;
}

.admin-menu a:hover {
    text-decoration: none;
    transform: scaleX(1.02);
}

.admin-new,
.admin-products {
    padding: 30px 0;
}

</style>
