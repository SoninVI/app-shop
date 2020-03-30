<template>
    <div class="v-cart-item">
        <div class="v-cart-item-img">
            <img :src="require('../assets/img/' + cart_item_data.image)" alt="">
        </div>
        <div class="v-cart-item__info">
            <p>{{cart_item_data.name}}</p>
            <p>{{cart_item_data.price}}</p>
            <p>{{cart_item_data.article}}</p>
        </div>
        <div class="v-cart-item__quantity">
            <p>qua</p>
            <span class="quantity_btn_minmax" @click="decrementItem">-</span>
            <span>{{cart_item_data.quantity}}</span>
            <span class="quantity_btn_minmax" @click="incrementItem">+</span>

        </div>
            <button @click="deleteFromCart">delete</button>

    </div>
</template>

<script>


    export default {
        name: "v-cart-item",
        data(){
            return{}
        },
        props:{
            cart_item_data:{
                type: Object,
                default(){
                    return{}
                }
            }
        },
        methods:{
            deleteFromCart(){
                this.$emit('deleteFromCart')
            },
            decrementItem(){
                this.$emit( 'decrement')
            },
            incrementItem(){
                this.$emit('increment')
            },
        },
        mounted() {
            this.$set(this.cart_item_data, 'quantity', 1)
        }
    }
</script>

<style>
    .v-cart-item{
        display: flex;
        justify-content: space-between;
        align-items: center;
        flex-wrap: nowrap;
    }
    .v-cart-item-img{
        width: 250px;
    }
    .v-cart-item-img>img{
        width: 100%;
    }
    .quantity_btn_minmax{
        cursor: pointer;
    }

</style>
