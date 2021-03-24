<template>
    <div>
        <Game />
    </div>
</template>

<script>
    import Vue from "vue";
    import Game from "./components/Game";
    export default Vue.extend({
        name: "App",
        components: {
            Game
        }
    });
</script>
