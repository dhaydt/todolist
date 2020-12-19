<template>
    <div>
        <h3>Task Available</h3>
        <div v-for="(item, index) in items" :key="index"></div>
        <list-item
        :item="item"
        class="item"
        />
    </div>
</template>

<script>
    import listItem from "./listItem"
    import ListItem from "./listItem.vue"
    export default {
        props: ['items'],
        components: {
            listItem,
        }
    }
</script>

<style scoped>
.item {
    background: #e6e6e6;
    padding: 5px;
    margin-top: 5px;
}
</style>
