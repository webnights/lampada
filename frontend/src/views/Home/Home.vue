<template>

    <Carousel :news = "news"/>
    <Hero/>
    <Advantages/>

</template>
<script>
    import Hero from '/src/components/Hero/Hero.vue';
    import Advantages from '/src/components/Advantages/Advantages.vue';
    import Carousel from '/src/components/Carousel/Carousel.vue';

    export default{
        components:{Hero,Advantages,Carousel},
        data(){
            return{
                news:[
                    {id: 1, image: '/src/assets/images/buses_carousel/slider1.jpg'},
                    {id: 2, image: '/src/assets/images/buses_carousel/slider2.jpg'},
                    {id: 3, image: '/src/assets/images/buses_carousel/slider3.jpg'},
                ]
            }
        }
    }
</script>