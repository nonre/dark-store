<template>
    <button class="btn">{{ title }}</button>
</template>

<script>
    export default {
        name: "Button",
        props: ['title'],
    }
</script>

<style lang="scss">
    .btn {
        font-family: 'RotondaC', sans-serif;
        display: inline-flex;
        align-items: center;
        justify-content: center;
        padding: 17px 110px;
        background: #7DB945;
        color: #ffffff;
        border-radius: 10px;
        font-weight: bold;
        font-size: 18px;
        line-height: 27px;
        text-align: center;
    }
</style>