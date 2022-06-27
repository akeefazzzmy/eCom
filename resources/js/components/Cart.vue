<template>
    <div>
        <li class="nav-item">
            <a href="/home" class="btn btn-warning btn-sm">
                Cart {{itemCount}}
            </a>
        </li>
    </div>
</template>

<script>
    export default{
        data(){
            return{
                itemCount: '',
            }
        },
        mounted(){
            this.$root.$on('changeInCart', (item)=>{
                this.itemCount = item;
            })
        },
        methods:{
            getCartItemOnPageLoad(){

            }
        },
        created(){
            this.getCartItemOnPageLoad(){
                let response = await axios.post('/cart');
            }
        }
    }
</script>
