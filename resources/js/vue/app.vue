<template>
    <div class="todoListContainer">
        <div class="heading">
            <h2 id="title">Todo List</h2>
            <add-item-form
            v-on:reloadlist="getList()"
            />
        </div>
        <div>
            <list-view :items="items"
            v-on:reloadlist="getList()"
            />
        </div>
    </div>
</template>

<script>
    import addItemForm from "./addForm"
    import listView from "./listView"

    export default {
        components: {
            addItemForm,
            listView,
        },
        data: function() {
            return{
                items: []
            }
        },
        methods: {
            getList () {
                axios.get('api/items')
                .then(response => {
                    this.items = response.data
                })
                .catch( error => {
                    console.log(error);
                })
            }
        },
        created() {
            this.getList();
        }
    }
</script>

<style scoped>
.todoListContainer {
    width: 350px;
    margin: auto;
}
.heading {
    background: #e6e6e6;
    padding: 10px;
    margin-top: 30px;
}

#title{
    text-align: center;
}
</style>
