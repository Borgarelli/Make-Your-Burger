<template>
    <div id="main-banner">
        <h1>Make Your Burguer</h1>
    </div>
</template>

<script>
    export default {
        name: 'Banner',
        data(){
            return {

            }
        }
    }
</script>

<style scoped>
    #main-banner{
        background-image: url('/public/img/burger.jpg');
        background-position: 0 -250px;
        background-size: cover;
        background-repeat: no-repeat;
        height: 500px;
        display: flex;
        align-items: center;
        justify-content: flex-start;
    }

    #main-banner h1 {
        color: white;
        text-align: center;
        font-size: 60px;
        text-shadow: 3px 3px 2px #222;
        background-color: rgba(2, 2, 2, 0.445);
        padding: 20px 40px;
    }
</style>