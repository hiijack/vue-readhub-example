<template>
    <List v-bind:list="hitTopics" v-on:toggleInfo="toggleInfo" />
</template>

<script>
    import List from './List';

    export default {
        name: 'HitTopics',
        props: ['hitTopics'],
        components: {
            List
        },
        methods: {
            toggleInfo(item) {
                this.$emit('toggleInfo', item);
            }
        }
    }

</script>