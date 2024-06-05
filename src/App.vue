<script >
import MainSection1 from './components/MainSection1.vue';
import Carousel from './components/Carousel.vue';
import CardContainer from './components/CardContainer.vue';
import Behavior from './components/Behavior.vue';




export default{
    components: {
        MainSection1,
        Carousel,
        Behavior,
        CardContainer,
        
    },
}

</script>

<template>
  <MainSection1/>
  <Carousel />
  <Behavior />
  
  <CardContainer />

</template>

<style >

</style>
