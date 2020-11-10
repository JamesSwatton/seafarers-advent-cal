<template>
    <div>
        <div
            class="w-48 h-48 bg-cover"
            :style="getContainer"
            v-if="!opened && day == 0"
        ></div>
        <button
            class="flex items-center justify-center w-48 h-48 bg-center bg-contain"
            :style="getDoor"
            v-else-if="!opened && day > 0"
            @click="clicked = true"
        >
            <p class="text-6xl font-extrabold text-white">{{ parseDay }}</p>
        </button>
        <!-- <img -->
        <!--     class="object-fill w-48 h-48" -->
        <!--     :src="require('../assets/container_' + getRandomAssetPath.src)" -->
        <!--     :alt="getRandomAssetPath.alt" -->
        <!--     v-if="!opened && day == 0" -->
        <!-- /> -->
        <!-- <div v-else-if="!opened && day > 0"> -->
        <!--     <img -->
        <!--         class="object-fill w-48 h-48 " -->
        <!--         :src=" -->
        <!--             require('../assets/container_door_' + -->
        <!--                 getRandomAssetPath.src) -->
        <!--         " -->
        <!--         :alt="getRandomAssetPath.alt" -->
        <!--         @click="clicked = true" -->
        <!--     /> -->
        <!--     <p class="text-6xl font-extrabold text-white ">{{ parseDay }}</p> -->
        <!-- </div> -->
        <div
            v-else
            class="flex items-center justify-center w-48 h-48 bg-gray-500"
        >
            <p class="text-3xl text-white underline">
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
            assetsList: [
                { src: "red.png", alt: "red container" },
                { src: "gray.png", alt: "gray container" },
                { src: "green.png", alt: "green container" },
                { src: "blue.png", alt: "blue container" },
                { src: "yellow.png", alt: "yellow container" }
            ],
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
        parseDay() {
            let day = this.day;
            if (day.length == 1) {
                day = "0 " + day;
            } else {
                day = day[0] + " " + day[1];
            }
            return day;
        },
        isCorrectDay() {
            const newDate = new Date();
            return this.day <= newDate.getDate() ? true : false;
        },
        getRandomAssetPath() {
            let randNum = Math.floor(Math.random() * this.assetsList.length);
            return this.assetsList[randNum];
        },
        getDoor() {
            return {
                backgroundImage: `url(${require("../assets/container_door_" +
                    this.getRandomAssetPath.src)})`
            };
        },
        getContainer() {
            return {
                backgroundImage: `url(${require("../assets/container_" +
                    this.getRandomAssetPath.src)})`
            };
        }
    }
};
</script>

<style scoped></style>
