<template>
    <div class="carousel-item">
        <img class="carousel-item__img" :src="require('../assets/images/' + itemData.img)" alt="">
        <div class="carousel-item__content">
            <h2 class="carousel-item__title">{{ itemData.title }}</h2>
            <p class="carousel-item__desc">{{ itemData.desc }}</p>
        </div>
    </div>
</template>

<script>
    export default {
        name: "CarouselItem",
        props: {
            itemData: {
                type: Object,
                default: () => {}
            }
        }
    }
</script>

<style lang="scss">
    .carousel-item{
        font-family: 'RotondaC', sans-serif;
        color: #26303B;
        font-size: 16px;
        line-height: 24px;
        margin: 0;
    }
    .carousel-item__content {
        padding-top: 28px;
    }
    .carousel-item__title {
        font-weight: bold;
    }
</style>