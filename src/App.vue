<template>
    <!-- <div id="app" class="overflow-hidden" :style="backgroundImage"> -->
    <!--     <ContainerList></ContainerList> -->
    <!-- </div> -->
    <div class="relative bg-gradient-to-b from-gray-700 to-gray-900">
        <img
            src="./assets/moon.png"
            alt="moon"
            class="absolute right-0 w-16 mt-16 mr-10 md:mr-24 lg:mt-24 lg:w-24"
        />
        <ContainerList></ContainerList>
    </div>
</template>

<script>
import ContainerList from "./components/ContainerList";
export default {
    name: "App",
    components: { ContainerList },
    computed: {
        backgroundImage() {
            return {
                backgroundImage: `url(${require("./assets/background.png")})`
            };
        }
    }
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
