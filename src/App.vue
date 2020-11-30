<template>
    <!-- <div id="app" class="overflow-hidden" :style="backgroundImage"> -->
    <!--     <ContainerList></ContainerList> -->
    <!-- </div> -->
    <div>
        <div id="background" class="fixed w-screen h-screen">
            <div class="h-64 bg-gray-900"></div>
            <div
                class="h-full bg-gradient-to-b from-gray-900 to-blue-200"
            ></div>
            <img
                src="./assets/moon.png"
                alt="moon"
                class="fixed top-0 right-0 z-0 w-16 pt-32 mr-10 md:mr-24 lg:w-24"
            />
        </div>
        <img
            src="./assets/ISWAN_Logo_White_NoStrap.png"
            alt="ISWAN logo"
            class="relative z-10 w-40"
        />
        <div class="relative z-10 w-5/6 pt-6 pb-16 mx-auto ">
            <p class="pb-8 text-5xl font-extrabold text-white">
                Festive Countdown!
            </p>
            <p class="text-2xl font-thin text-white ">
                As part of this year’s #SeafarersDeliveringChristmas campaign,
                you can follow our Festive Countdown for seafarers throughout
                December! Behind each door is a prize giveaway, an idea for an
                onboard activity or something fun for you to enjoy, whether you
                are working during the holiday season or spending time with your
                family. Wishing you all a happy, healthy festive season!
            </p>
        </div>
        <ContainerList></ContainerList>
    </div>
</template>

<script>
import ContainerList from "./components/ContainerList";
export default {
    name: "App",
    components: { ContainerList }
    //computed: {
    //    backgroundImage() {
    //        return {
    //            backgroundImage: `url(${require("./assets/background.png")})`
    //        };
    //    }
    //}
};
</script>

<style>
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
}
</style>
