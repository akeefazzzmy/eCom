<template>
    <div class="container">
        <hr>
        <button class="btn btn-warning text-center"
            v-on:click.prevent="addProductToCart()">
            Add To Cart
        </button>
    </div>
</template>

<script>
    export default{
        
        // data, props, method start min 01:02:41

        data(){

        },

        props:[
            'productId',
            'userId'
        ],

        methods:{
            async addProductToCart(){

                //check if user logged in start min 1:8:8


                //start min 1:6:42
                //this fx need to recompile by npm run dev
                if(this.userId == 0){
                    this.$toastr.e('You need to login to add this product in Cart');
                    return;
                }

                // if user logged in then add item to cart start min 1:8:27
                // check axios has been installed or not, check window.axios=require('axios'); in resources/components/bootstrap.js
                //if want to use await, need to use async
                let response = await axios.post('/cart', {
                    'product_id':this.productId
                });
                
                this.$root.$emit('changeInCart', response.data.items);//items come from cartscontroller
            }
        },

        mounted(){
            console.log('Component mounted.')
        }
    }
</script>
