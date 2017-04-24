<template>
    <div>
        <div class="container" v-for="(item, index) in list" v-on:click="toggleInfo(item)">
            <Item v-bind:item="item" v-bind:isLast="index != list.length - 1" />
        </div>
    </div>
</template>

<script>
    import Item from './Item';

    export default {
        name: 'List',
        props: ['list'],
        components: {
            Item
        },
        methods: {
            toggleInfo(item) {
                this.$emit('toggleInfo', item);
            }
        }
    }

</script>

<style scoped>
    .container {
        margin-top: 15px;
        margin-left: 15px;
        margin-right: 15px;
    }
</style>
