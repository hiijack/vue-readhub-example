<template>
    <List v-bind:list="news" v-on:toggleInfo="toggleInfo" />
</template>

<script>
    import List from './List';

    export default {
        name: 'HitTopics',
        props: ['news'],
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