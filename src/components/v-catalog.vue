<template>
    <div class="v-catalog">
        <router-link :to="{name: 'cart', params: {cart_data: CART}}">
            <div class="v-catalog__link_to_cart">
                cart: {{CART.length}}
            </div>
        </router-link>

        <h1>Catalog</h1>
       <div class="v-catalog-list">
            <v-catalog-item
                v-for="product in PRODUCTS"
                :key="product.article"
                :product_data="product"
                @addToCart="addToCart"
            />
       </div>
    </div>
</template>

<script>
    import vCatalogItem from './v-catalog-item'
    import {mapActions, mapGetters} from 'vuex'

    export default {
        name: "v-catalog",
        components:{
            vCatalogItem
        },
        computed:{
            ...mapGetters([
                'PRODUCTS',
                'CART'
            ])
        },
        methods:{
            ...mapActions([
                'GET_PRODUCTS_FROM_API',
                'ADD_TO_CART'
            ]),
            addToCart(data){
              this.ADD_TO_CART(data)
          }
        },
        mounted() {
            this.GET_PRODUCTS_FROM_API()
            .then((response)=>{
                if (response.data){
                    console.log('data array')
                }
            })
        },
        data() {
            return {

            }
        }
    }
</script>

<style>
    .v-catalog-list{
        display: flex;
        flex-wrap: wrap;
        flex-basis: 25%;
        justify-content: space-between;
    }
    .v-catalog__link_to_cart{
        position: absolute;
        top: 10px;
        right: 10px;
        padding: 15px;
        border: 1px solid rebeccapurple;
        cursor: pointer;
    }
</style>
