<template>
    <div @click="$emit('click')">
        <button class="square"><span v-if="value !== ''">{{value}}</span></button>
    </div>
</template>

<script>
    import Vue from "vue";

    export default Vue.extend({
        name: "Square",
        props: {
            value: {
                type: String
            },
        }
    });
</script>

<style lang="scss">
.square {
    width: 100px;
    height: 100px;
    font-size: 60px;
    font-weight: bold;
    font-family:Arial, Helvetica, sans-serif;
    background-color: rgb(99, 192, 131);
    border: 1px solid rgb(99, 192, 131);
    border-radius: 15px;
    box-shadow: 1px 1px 5px rgb(77, 108, 77);
    margin: 5px;
    cursor: pointer;
    &:active {
        box-shadow: 1px 1px 1px rgb(77, 108, 77);
    }
    &:focus {
        border: hidden;
        outline: none;
    }
}
</style>