<template>
    <div @click="clicked = true">
        <img
            class="object-fill w-48 h-48"
            src="./assets/container_door_blue.png"
            alt="container_door_blue"
            v-if="!opened"
        />
        <div v-else class="w-48 h-48 bg-gray-500">
            <p class="text-3xl text-center text-white">
                <a :href="link">ISWAN</a>
            </p>
        </div>
    </div>
</template>

<script>
export default {
    name: "Container",
    props: ["day"],
    data() {
        return {
            link: "https://www.seafarerswelfare.org/",
            assetsList: [],
            clicked: false,
            opened: false
        };
    },
    watch: {
        clicked() {
            if (this.clicked && this.isCorrectDay) this.opened = true;
        }
    },
    computed: {
        isCorrectDay() {
            const newDate = new Date();
            return this.day >= newDate.getDate() ? true : false;
        }
    }
};
</script>

<style scoped></style>
