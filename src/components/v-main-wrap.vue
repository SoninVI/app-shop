<template>
    <div class="v-main-wrap">
        <keep-alive>
            <router-view></router-view>
        </keep-alive>
    </div>
</template>

<script>
     export default {
        name: 'v-main-wrap',
        data(){
            return{
                title: 'Main wrap'
            }
        },

    };
</script>

<style>
    .v-main-wrap{
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        max-width: 900px;
        margin: 0 auto;
    }
</style>
