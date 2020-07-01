<!--Child-->

<template>
    <div id="btns">
        <button type="button" class="btn btn-dark" v-on:click="$emit('increment')" >{{ buttonText }}</button>
    </div>
</template>

<script>
export default {
    name: "Buttons",
    props: {
        buttonText: String,
    },   
}
</script>

<style scoped>
    button{
        margin: 8px;
    }

</style>