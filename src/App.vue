<script >
import SectionTextImg from './components/SectionTextImg.vue';
import Carousel from './components/Carousel.vue';
import CardContainer from './components/CardContainer.vue';
import Behavior from './components/Behavior.vue';
import BestTutor from './components/BestTutor.vue';
import AppHeader from './components/AppHeader.vue';
import PageFooter from './components/PageFooter/PageFooter.vue';








export default{
    components: {
        SectionTextImg,
        Carousel,
        Behavior,
        CardContainer,
        BestTutor,
        AppHeader,
        PageFooter,
        
    },
}

</script>

<template>
  <AppHeader/>
  <SectionTextImg/>
  <Carousel />
  <Behavior />
  <CardContainer />
  <BestTutor />
  <PageFooter />
</template>

<style >

</style>
