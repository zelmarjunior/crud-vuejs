<template>
    <div class="register-button" v-on:click='registerOpen'>
        <p>+</p>
    </div>
</template>

<script>
export default {
    name: "SearchButton",
};
</script>

<style scoped>
p {
    margin: 0;
    padding: 0;
    text-align: center;
    color: white;
}
.register-button {
    display: flex;
    justify-content: center;
    align-content: center;
    /* border: solid 1px#545454; */
    background-color: #545454;
    border-radius: 50%;
    width: 50px;
    height: 50px;
    font-size: 44px;
    cursor: pointer;
}
</style>