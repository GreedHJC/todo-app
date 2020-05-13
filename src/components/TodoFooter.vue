<template>
<!--    <button v-on:click="clearTodoItems">clear</button>-->
    <button v-on:click="$emit('clear')">clear</button>

</template>

<script>

    export default {
        // methods: {
            // clearTodoItems : function () {
            //     this.$emit('clear');
            // }
        // },
    }
</script>

<style scoped>

</style>