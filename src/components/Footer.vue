<template>
    <footer id="footer">
        <p>Make Your burger &copy; 2022</p>
    </footer>
</template>

<script>
    export default {
        name: 'Footer'
    }
</script>

<style scoped>
    #footer{
        height: 200px;
        background-color: #222;
        border-top: 4px solid #111;
        color: #FCBA03;
        display: flex;
        align-items: center;
        justify-content: center;
        width: 100%;
        transition: .5s;
    }

    #footer:hover{
        color: white;
    }
</style>