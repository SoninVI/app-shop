<template>
    <div class="v-cart">
        <router-link :to="{name: 'catalog', params: {cart_data: CART}}">
            <div class="v-catalog__link_to_cart">
               back to catalog
            </div>
        </router-link>
        <h2>Корзина</h2>
        <p v-if="!cart_data.length">в корзине нет товара</p>
        <v-cart-item
            v-for="(item, index) in cart_data"
            :key="item.article"
            :cart_item_data="item"
            @deleteFromCart="deleteFromCart(index)"
            @increment="increment(index)"
            @decrement="decrement(index)"
        />
        <div class="v-cart-total">
            <p>total:</p>
            <p>{{CartTotal}} грн</p>
        </div>
    </div>
</template>

<script>
    import vCartItem from './v-cart-item'
    import {mapActions} from 'vuex'
    import {mapGetters} from 'vuex'
    export default {
        name: "v-cart",
        components:{
           vCartItem
        },
        data(){
            return{}
        },
        computed:{
          CartTotal(){
              let result = [];
              if(this.cart_data.length){
                  for( let item of this.cart_data){
                      result.push(item.price* item.quantity)
                  }
                  result= result.reduce(function (sum, el) {
                      return sum+el;
                  });
                  return result
              }else {
                  return 0
              }


          }
        },
        methods:{
            ...mapActions([
                'DELETE_FROM_CART',
                'INCREMENT_CART_ITEM',
                'DECREMENT_CART_ITEM'
            ]),
            ...mapGetters([
                'CART'
            ]),
            deleteFromCart(index){
                this.DELETE_FROM_CART(index)
            },
            increment(index){
                this.INCREMENT_CART_ITEM(index)
            },
            decrement(index){
                this.DECREMENT_CART_ITEM(index)
            },
        },
        props:{
            cart_data:{
                type: Array,
                default() {
                    return []
                }
            }
        }
    }
</script>

<style scoped>
    .v-cart{
        width: 100%;
    }
    .v-cart-total{
        position: fixed;
        bottom: 0;
        width: 100%;
        padding: 15px;
        display: flex;
        align-items: center;
        background: aqua;
        color: black;
        justify-content: center;
        font-size: 20px;
    }
    .v-cart-total>p{
        margin-right: 40px;

    }
</style>
