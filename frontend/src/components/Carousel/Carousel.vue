<template>
  <section class="buses__carousel">
    <div class="container">
      <div class="carousel__wrapper">
        <div
          class="carousel__inner"
          :style="{ transform: 'translateX(-' + 1320 * currentSlide + 'px)' }"
        >
          <CarouselItem
            v-for="(item, index) in news"
            :key="index"
            :item="item"
          />
        </div>
      </div>
      <div class="dots">
        <span
          v-for="(item, index) in news"
          :key="index"
          :class="index === currentSlide ? 'dot active' : 'dot'"
        ></span>
      </div>
    </div>
    <div class="carousel__arrow right" @click="nextSlide">
      <img :src="arrowRight" alt="" />
    </div>
    <div class="carousel__arrow left" @click="prevSlide">
      <img :src="arrowLeft" alt="" />
    </div>
  </section>
</template>

<script>
import CarouselItem from "/src/components/CarouselItem/CarouselItem.vue";
import arrowRight from "/src/assets/images/slider_arrow-right.svg";
import arrowLeft from "/src/assets/images/slider_arrow-left.svg";
export default {
  components: {
    CarouselItem,
  },
  props: {
    news: {
      type: Array,
    },
  },
  data() {
    return {
      currentSlide: 0,
      arrowRight: arrowRight,
      arrowLeft: arrowLeft,
    };
  },
  methods: {
    prevSlide() {
      if (this.currentSlide > 0) {
        this.currentSlide--;
      }
    },
    nextSlide() {
      if (this.currentSlide < this.news.length - 1) {
        this.currentSlide++;
      }
    },
  },
};
</script>
