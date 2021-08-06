<template>
    <div class="container">
        <span class="container__id">{{ num }}</span>
        <div class="wrapper">
            <div class="carousel" :style="{ 'margin-left': '-' + (100 * currentSlide) + '%'}">
                <CarouselItem
                        v-for="item in carouselData"
                        :key="item.id"
                        :item-data="item"
                />
            </div>
        </div>
        <button class="carousel-btn carousel-btn__prev" @click="prevSlide">
            <svg width="24" height="44" viewBox="0 0 24 44" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M2 2L22 22L2 42" stroke="#D0D5CD" stroke-width="3" stroke-linecap="round" stroke-linejoin="round"/>
            </svg>
        </button>
        <button class="carousel-btn carousel-btn__next" @click="nextSlide">
            <svg width="24" height="44" viewBox="0 0 24 44" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M2 2L22 22L2 42" stroke="#D0D5CD" stroke-width="3" stroke-linecap="round" stroke-linejoin="round"/>
            </svg>
        </button>
    </div>

</template>

<script>
    import CarouselItem from "./CarouselItem";
    export default {
        name: "Carousel",
        components: {
            CarouselItem
        },
        props: {
            carouselData: {
                type: Array,
                default: () => []
            }
        },
        data() {
            return {
                currentSlide: 0,
                num: 1,
            }
        },
        methods: {
            prevSlide() {
                if (this.currentSlide > 0) {
                    this.currentSlide--;
                    this.num--;
                }
            },
            nextSlide() {
                if (this.currentSlide >= this.carouselData.length - 1) {
                    this.currentSlide = 0;
                    this.num = 1;
                } else {
                    this.currentSlide++;
                    this.num++;
                }
            },
        }
    }
</script>

<style lang="scss">
    .container, .wrapper {
        max-width: 560px;
        margin: 0 auto;
    }
    .wrapper {
        overflow: hidden;
    }
    .container {
        position: relative;
        padding: 40px;
        background: #ffffff;
        box-shadow: 0 0 40px rgba(0, 0, 0, 0.1);
        border-radius: 10px;
        margin-bottom: 50px;
    }
    .container__id {
        font-family: 'RotondaC', sans-serif;
        display: block;
        position: absolute;
        top: 30px;
        left: 35px;
        font-weight: bold;
        font-size: 22px;
        line-height: 209%;
        text-align: center;
        width: 50px;
        height: 50px;
        border-radius: 50%;
        color: #7DB945;
        background: #ffffff;
    }
    .carousel {
        display: flex;
        transition: all ease 0.3s;
    }
    .carousel-btn {
        position: absolute;
        transform: translateY(-50%);
    }
    .carousel-btn__prev {
        top: 50%;
        left: -60px;
        svg {
            transform: rotate(180deg);
        }
    }
    .carousel-btn__next {
        top: 50%;
        right: -60px;
    }
</style>