<template>
    <div id="app">
        <div id="background" class="fixed w-screen h-screen">
            <div class="h-64 bg-gray-900"></div>
            <div
                class="h-full bg-gradient-to-b from-gray-900 to-blue-200"
            ></div>
            <img
                src="./assets/moon.png"
                alt="moon"
                class="fixed top-0 right-0 z-0 w-12 pt-32 mr-10 md:w-16 md:mr-24 lg:w-24"
            />
            <img
                src="./assets/stars.png"
                alt="stars"
                class="fixed top-0 right-0 w-screen px-10 mt-3"
            />
        </div>
        <img
            id="logo"
            src="./assets/ISWAN_Logo_White_NoStrap.png"
            alt="ISWAN logo"
            class="relative z-10 w-24 md:w-40"
        />
        <div class="relative z-10 w-5/6 pt-6 pb-16 mx-auto ">
            <p class="pb-8 text-3xl font-extrabold text-white md:text-5xl">
                Festive Countdown!
            </p>
            <p class="font-thin text-white text-md md:text-xl lg:text-2xl ">
                As part of this year’s #SeafarersDeliveringChristmas campaign,
                you can follow our Festive Countdown for seafarers throughout
                December! Behind each door is a prize giveaway, an idea for an
                onboard activity or something fun for you to enjoy, whether you
                are working during the holiday season or spending time with your
                family. Wishing you all a happy, healthy festive season!
            </p>
        </div>
        <ContainerList></ContainerList>
        <div class="relative z-10 flex justify-center mb:4 md:mb-8">
            <p class="pt-1 pr-4 text-sm text-white md:text-lg ">
                Made by James Swatton
            </p>
            <a href="https://www.github.com/jamesswatton">
                <img
                    src="./assets/GitHub-Mark-Light-64px.png"
                    alt="James Swatton's
                GitHub profile"
                    class="w-6 h-6 md:w-8 md:h-8"
                />
            </a>
            <a class="ml-3" href="mailto: jamesstanleyswatton@gmail.com">
                <svg
                    xmlns="http://www.w3.org/2000/svg"
                    viewBox="0 0 24 24"
                    class="w-6 h-6 text-white fill-current md:w-8 md:h-8"
                >
                    <path
                        d="M20 4H4c-1.1 0-1.99.9-1.99 2L2 18c0 1.1.9 2 2 2h16c1.1 0 2-.9 2-2V6c0-1.1-.9-2-2-2zm0 4l-8 5-8-5V6l8 5 8-5v2z"
                    />
                </svg>
            </a>
        </div>
    </div>
</template>

<script>
import ContainerList from "./components/ContainerList";
export default {
    name: "App",
    components: { ContainerList }
};
</script>

<style>
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    color: #2c3e50;
}
</style>
