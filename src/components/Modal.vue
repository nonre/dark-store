<template>
    <div class="modal">
        <div class="modal__content">
            <span class="modal__close"
                @click="closeModal"
            ></span>
            <slot></slot>
        </div>
    </div>
</template>

<script>
    export default {
        name: "Modal",
        methods: {
            closeModal() {
                this.$emit('closeModal')
            }
        }
    }
</script>

<style lang="scss">
    .modal {
        justify-content: center;
        align-items: center;
        position: fixed;
        top: 0;
        right: 0;
        bottom: 0;
        left: 0;
        background: rgba(0,0,0,0.5);
    }
    .modal__content {
        position: relative;
        margin: 122px 60px 0 140px;
        background: #ffffff;
        color: #2e2e2e;
        font-size: 25px;
        padding: 80px 40px 60px 40px;
        border-radius: 10px;
    }
    .modal__form {
        font-family: 'RotondaC', sans-serif;
        display: flex;
        flex-direction: column;
        align-items: center;

        input {
            width: 100%;
            margin-bottom: 20px;
            height: 30px;
        }
    }
    .modal__btn {
        width: fit-content;
    }
    .modal__message {
        font-weight: bold;
    }
    .modal__err {
        font-size: 20px;
        margin-bottom: 15px;
    }
    .modal__form-name {
        margin-bottom: 20px;
        font-size: 20px;
    }
    .modal__close {
        position: absolute;
        right: 30px;
        top: 20px;
        width: 25px;
        height: 25px;
        cursor: pointer;
    }
    .modal__close:before, .modal__close:after {
        position: absolute;
        left: 15px;
        content: "";
        height: 25px;
        width: 3px;
        background-color: #272727;
    }
    .modal__close:before {
        transform: rotate(45deg);
    }
    .modal__close:after {
        transform: rotate(-45deg);
    }
</style>