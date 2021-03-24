<template>
    <div>
        <h1>{{title}}</h1>
        <Board />
    </div>
</template>

<script>
    import Vue from "vue";
    import Board from "./Board";

    export default Vue.extend({
        name: "Game",
        components: {
            Board
        },
        data() {
            return {
                title: 'Tic Tac Toe with Vue',
            }
        }
    });
</script>

<style lang="scss">
h1 {
    font-size: 60px;
    font-weight: bold;
    font-family:Arial, Helvetica, sans-serif;
    color: rgb(99, 192, 131);
    background-color: #FFF;
    text-shadow: 0px 2px 2px rgb(77, 108, 77);
}
</style>
