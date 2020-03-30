<template>
    <div class="v-catalog-item">
        <div class="v-catalog-img">
            <img :src="require('../assets/img/' + product_data.image)" alt="">
        </div>
        <p class="v-catalog-item__name">{{product_data.name}}</p>
        <p class="v-catalog-item__price">{{product_data.price}} грн</p>
        <button class="v-catalog-item__btn btn"
                @click='addToCart'>
            add to cart
        </button>
    </div>
</template>

<script>
    export default {
        name: "v-catalog-item",
        props:{
            product_data: {
                type: Object,
                default(){
                    return {}
                }
            }
        },
        methods:{
            addToCart(){
                this.$emit('addToCart',this.product_data);
            }
        },
        data(){
            return {}
        }
    }
</script>

<style>
    .v-catalog-item{
        flex-basis: 25%;
        margin-bottom: 15px;
        border: 1px solid red;
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        align-items: center;
        padding: 10px;
    }
    .v-catalog-img{
        width: 200px;
        margin: 0 auto;
        flex-grow: 1;
    }
    .v-catalog-img>img{
        width: 100%;
        display: block;
    }
</style>
