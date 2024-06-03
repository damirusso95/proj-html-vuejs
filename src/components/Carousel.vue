<script>
export default {
  name: 'Carousel',
  data() {
    return {
      currentIndex: 0,
      slides: [
        {
          imgSrc: new URL('../assets/img/testimonials-standard-1.png', import.meta.url).href,
          text: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Minus maxime et quasi ad quidem nam vero voluptate temporibus, porro obcaecati sapiente expedita consequatur fugiat a ullam, molestias consequuntur ex debitis.',
          subText1: 'testo',
          subText2: 'altro testo'
        },
        {
          imgSrc: new URL('../assets/img/testimonials-standard-2.png', import.meta.url).href,
          text: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Minus maxime et quasi ad quidem nam vero voluptate temporibus, porro obcaecati sapiente expedita consequatur fugiat a ullam, molestias consequuntur ex debitis.',
          subText1: 'testo',
          subText2: 'altro testo'
        },
        {
          imgSrc: new URL('../assets/img/testimonials-standard-3.png', import.meta.url).href,
          text: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Minus maxime et quasi ad quidem nam vero voluptate temporibus, porro obcaecati sapiente expedita consequatur fugiat a ullam, molestias consequuntur ex debitis.',
          subText1: 'testo',
          subText2: 'altro testo'
        }
      ]
    };
  },
  methods: {
    goToSlide(index) {
      this.currentIndex = index;
    }
  }
};
</script>

<template>
  <div class="JS_bg">
    <div class="container d-flex flex-column align-items-center">
      <div v-for="(slide, index) in slides" :key="index" v-show="index === currentIndex">
        <img :src="slide.imgSrc" alt="Slide image" class="rounded-circle">
        <p>{{ slide.text }}</p>
        <p>{{ slide.subText1 }}</p>
        <p>{{ slide.subText2 }}</p>
      </div>
      <div class="bottoni">
        <button v-for="(slide, index) in slides" :key="index" :class="{ active: index === currentIndex }"
          @click="goToSlide(index)" class="indicator"></button>
      </div>
    </div>
  </div>
</template>

<style scoped>
.JS_bg {
  width: 100%;
  background-image: url('../assets/img/h5-parallax-img-1.png');
  background-size: cover;
  padding: 2rem 0;
}

.carousel-indicators {
  display: flex;
  justify-content: center;
  margin-top: 1rem;
}

.carousel-indicators .indicator {
  background-color: #000;
  border: 2px;
  width: 20px;
  height: 20px;
  border-radius: 50%;
  margin: 0 5px;
  cursor: pointer;
}

.carousel-indicators .indicator.active {
  background-color: #000000;
}

.bottoni{
  width: 3rem;
  height: 3rem;
  border-radius: 50%;
  border: 2px;
  
}
</style>
