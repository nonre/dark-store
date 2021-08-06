<template>
  <Carousel
    :carousel-data="sliderItems"
  />
  <Button
    @click="showModal"
    title="К покупкам"
  ></Button>
  <Modal
    v-if="isModalVisible"
    @closeModal="closeModal"
  >
    <form class="modal__form" @submit.prevent="checkForm($event, email); post();" novalidate="true"
    >
      <div class="modal__form-content"
        v-if="!isSubmitted"
      >
        <div class="modal__err" v-if="errors.length">
          <ul>
            <li v-for="(error, index) in errors" :key="index">{{ error }}</li>
          </ul>
        </div>
        <input type="email" v-model="email" placeholder="E-mail">
        <Button
                title="Отправить"
        ></Button>
      </div>
      <p class="modal__message">{{ message }}</p>
    </form>
  </Modal>
</template>

<script>
import Carousel from './components/Carousel.vue'
import Modal from "./components/Modal";
import Button from "./components/Button";

export default {
  name: 'App',
  data() {
    return {
      errors:[],
      isModalVisible: false,
      isValid: true,
      isSubmitted: false,
      email: "",
      message: "",
      buttonData: "",
      sliderItems: [
        { id: 1, title: 'Привезём точно по списку', desc: 'Сборщик берëт с собой наручный терминал, на котором он видит весь список покупок для каждого заказа.', img: '1.jpg'},
        { id: 2, title: 'Собираем быстро и эффективно', desc: 'Для улучшения эргономики пространства товары размещены от тяжëлых к лëгким, находящимся уже в конечной зоне упаковки.', img: '2.jpg'},
        { id: 3, title: 'За свежесть и качество отвечаем', desc: 'Выделены специальные зоны, в том числе холодная и морозильная.', img: '3.jpg'},
        { id: 4, title: 'Шампунь не положат рядом с рыбой', desc: 'Собираем и упаковываем ваш заказ с заботой: соблюдаем принципы товарного соседства и учитываем вес товара.', img: '4.jpg'},
        { id: 5, title: 'Довезëм в сохранности даже яйца', desc: 'Бережно транспортируем контейнеры, фиксируя их стяжными ремнями. Системы охлаждения поддерживают температурный режим.', img: '5.jpg'},
      ]
    }
  },
  components: {
    Button,
    Carousel,
    Modal
  },
  methods: {
    showModal() {
      this.isSubmitted = false;
      this.isModalVisible = true
    },
    closeModal() {
      this.isModalVisible = false;
      this.message = ""
    },
    post() {
      if (this.isValid) {
        const response = new Promise((resolve) => {
          setTimeout(() => resolve("Спасибо"), 500)
        });
        response.then(data => {
          this.message = data;
          this.isSubmitted = true;
        });
      }
    },
    checkForm(e, text) {
      this.errors = [];
      this.isValid = true;

      if (!this.email) {
        this.errors.push('Укажите электронную почту.');
        this.isValid = false;
      } else if (!this.validEmail(this.email)) {
        this.errors.push('Укажите корректный адрес электронной почты.');
        this.isValid = false;
      }
      if (!this.errors.length) {
        console.log(text);
        return true;
      }
      e.preventDefault();
    },
    validEmail: function (email) {
      const re = /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
      return re.test(email);
    }
  }
}
</script>

<style lang="scss">
  @import "assets/css/main.css";
  @import "assets/css/reset.css";

 #app {
  text-align: center;
  margin-top: 50px;
  }
</style>
