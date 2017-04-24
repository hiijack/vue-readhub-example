<template>
    <div class="load">
        <a href="javascript:;">点击加载更多</a>
    </div>
</template>

<script>
    export default {
        name: 'LoadButton'
    }

</script>

<style scoped>
    .load {
        width:50%;
        margin: 40px auto 10px auto;
        text-align: center;
        font-size: 16px;
    }
    .load a {
        text-decoration: none;
        color: #607d8b;
        -webkit-tap-highlight-color: rgba(0,0,0,0);   
    }
</style>