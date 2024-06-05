<script>
export default {
  name: 'Carousel',
  data() {
    return {
      currentIndex: 0,
      timer: null,
      slides: [
        {
          imgSrc: new URL('../assets/img/testimonials-standard-1.png', import.meta.url).href,
          text: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Minus maxime et quasi ad quidem nam vero voluptate temporibus, porro obcaecati sapiente expedita consequatur fugiat a ullam, molestias consequuntur ex debitis.',
          subText1: 'Virginia Foster',
          subText2: 'STUDENT'
        },
        {
          imgSrc: new URL('../assets/img/testimonials-standard-2.png', import.meta.url).href,
          text: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Minus maxime et quasi ad quidem nam vero voluptate temporibus, porro obcaecati sapiente expedita consequatur fugiat a ullam, molestias consequuntur ex debitis.',
          subText1: 'Molly Simons',
          subText2: 'TEACHER'
        },
        {
          imgSrc: new URL('../assets/img/testimonials-standard-3.png', import.meta.url).href,
          text: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Minus maxime et quasi ad quidem nam vero voluptate temporibus, porro obcaecati sapiente expedita consequatur fugiat a ullam, molestias consequuntur ex debitis.',
          subText1: 'Joan Collins',
          subText2: 'STUDENT'
        }
      ]
    };
  },
  methods: {
    goToSlide(index) {
      this.currentIndex = index;
    },
    nextSlide() {
      if (this.currentIndex + 1 >= this.slides.length) {
        this.currentIndex = 0;
      } else {
        this.currentIndex++;
      }
    },
    startAutoScroll() {
      this.timer = setInterval(this.nextSlide, 3000);
    },
    stopAutoScroll() {
      clearInterval(this.timer);
    }
  },
  mounted() {
    this.startAutoScroll();
  },
  beforeDestroy() {
    this.stopAutoScroll();
  }
};
</script>

<template>
  <div class="CS_bg">
    <div class="container d-flex flex-column align-items-center w-50 text-center">
      <div class="py-5" v-for="(slide, index) in slides" :key="index" v-show="index === currentIndex">
        <img :src="slide.imgSrc" alt="Slide image">
        <p class="py-5">{{ slide.text }}</p>
        <p>{{ slide.subText1 }}</p>
        <p>{{ slide.subText2 }}</p>
      </div>
      <div class="button-container py-5">
        <button v-for="(slide, index) in slides" :key="index" :class="{ active: index === currentIndex }"
          @click="goToSlide(index)" class="indicator"></button>
      </div>
    </div>
  </div>
</template>

<style scoped>
/* Stile per il contenitore principale del carosello con effetto parallax */
.CS_bg {
  width: 100%;
  background-image: url('../assets/img/h5-parallax-img-1.png');
  background-size:cover;
  background-attachment: fixed; 
  padding: 2rem 0;
  height: 100vh; 
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
}

/* Stile per il bottone attivo */
.indicator.active {
  background-color: #ffffff;
}

/* Stile per il contenitore dei bottoni di navigazione */
.button-container {
  width: 5rem;
  display: flex;
  justify-content: space-around;
}

/* Stile per ogni indicatore (bottone di navigazione) */
.indicator {
  width: 15px;
  height: 15px;
  border-radius: 50%;
  background-color: rgba(255, 255, 255, 0.50);
  border: none;
  cursor: pointer;
}
</style>
