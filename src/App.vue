<template>
    <div id="app" class="overflow-hidden" :style="backgroundImage">
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
    max-height: 1920px;
}
</style>
