<template>
  <div class="product">
    <a :href="product.link" target="_blank" class="product__link">
      <img :src="product.icon" alt="" />
      <h6>{{ product.name }}</h6>
    </a>
    <div class="cart_info">
      <label
        >Стоимость
        <h2 class="price">
          {{ " " + product.price + " " + "₽" }}
        </h2></label
      >
      <label v-if="ISAUTHORIZED"
        >Количество:
        <input
          type="number"
          min="1"
          class="quantity"
          v-model="quantity"
          @input="validate($event)"
      /></label>
      <button @click="addToCart" class="button" v-if="ISAUTHORIZED">
        Добавить в корзину
      </button>
      <span v-if="!ISAUTHORIZED" class="please_login"
        >Зарегистрируйтесь, чтобы добавить товар в корзину</span
      >
    </div>
  </div>
</template>
<script>
import { mapGetters } from "vuex";
import { mapMutations } from "vuex";
import axios from "axios";
export default {
  props: {
    product: {
      type: Object,
      required: true,
    },
  },
  data() {
    return {
      products: [],
      quantity: 1,
    };
  },
  methods: {
    ...mapMutations(["setCartSize"]),
    async getProducts() {
      const response = await axios.get("http://localhost:3000/products");
      this.products = response.data;
    },
    async addToCart() {
      const body = {
        user_id: this.USERID,
        cart_id: this.USERID,
        product_id: this.product.id,
        quantity: this.quantity,
      };
      try {
        const response = await axios.post("http://localhost:3000/cart", body);
        this.updateTotalQuantity();
        alert(response.data.message);
      } catch (error) {
        if (
          error.response &&
          error.response.data &&
          error.response.data.error
        ) {
          alert(error.response.data.error);
        } else {
          alert("Ошибка");
        }
      }
    },
    async updateTotalQuantity() {
      const userId = this.USERID;
      const response = await axios.get(`http://localhost:3000/cart/${userId}`);
      const total = response.data.reduce((acc, item) => {
        return acc + item.product_quantity;
      }, 0);
      this.setCartSize(total);
    },
    validate($event) {
      if ($event.target.value < 1) {
        $event.target.value = 1;
      }
    },
  },
  beforeMount() {
    this.getProducts();
  },
  computed: {
    ...mapGetters(["USERID", "ISAUTHORIZED"]),
    productBackgroundStyle() {
      return {
        background: `url(${this.product.image}) 0 0 / cover no-repeat`,
        height: "250px",
        width: "350px",
      };
    },
  },
};
</script>
