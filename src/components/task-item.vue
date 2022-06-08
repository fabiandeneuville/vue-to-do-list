<template>

    <div class="item-todo">
        <p>{{ task }}</p>
        <button v-on:click="deleteTask" class="delete-btn">X</button>
    </div>

</template>

<script>

export default {
    name: 'taskItem',
    props: ['task', 'deleteTask']
}

</script>

<style scoped>

    .item-todo {
        width:100%;
        position: relative;
        margin-bottom:10px;
        background: #f1f1f1;
        padding: 15px;
        border-radius:5px;
        overflow: hidden;
        box-shadow: 8px 10px 9px -2px #9E9E9E;
    }

    .item-todo p {
        text-align: left;
        padding:0 10px
    }

    .delete-btn {
        position: absolute;
        top:0px;
        right: 0px;
        width:25px;
        border: none;
        cursor: pointer;
        color: crimson;
    }

</style>