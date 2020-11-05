<template>
    <div>
        <ContainerList></ContainerList>
    </div>
</template>

<script>
import ContainerList from "./ContainerList";
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
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
}
</style>
