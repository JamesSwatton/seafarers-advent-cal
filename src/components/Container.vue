<template>
    <div class="w-24 h-24 shadow-2xl box-border md:w-32 md:h-32 lg:w-48 lg:h-48">
        <div
            class="w-full h-full bg-cover "
            :style="getContainer"
            v-if="!opened && day == 0"
        ></div>
        <button
            class="flex items-center justify-center w-full h-full bg-center bg-contain"
            :style="getDoor"
            v-else-if="!opened && day > 0"
            @click="clicked = true"
        >
            <p
                class="inline-block w-full text-3xl font-extrabold text-center text-white hover:scale-110 transform hover:text-gray-800 md:text-6xl"
            >
                {{ parseDay }}
            </p>
        </button>
        <div v-else class="relative w-full h-full bg-gray-800">
            <p
                class="absolute top-0 right-0 mt-1 mr-3 text-2xl text-white opacity-75 md:text-3xl md:mt-2 md:mr-4 lg:mt-6 lg:mr-8"
            >
                {{ day }}
            </p>
            <div
                class="absolute top-0 left-0 flex flex-col items-center justify-center w-full h-full bg-cover "
                :style="getOpenDoor"
            >
                <a :href="link" class="hover:scale-125 transform">
                    <img
                        src="../assets/door_stars.png"
                        alt="question mark"
                        class="h-10 md:h-12 lg:h-20"
                    />
                </a>
                <!-- <p class="text-xl text-white underline md:text-3xl"> -->
                <!--     <a :href="link">Hello</a> -->
                <!-- </p> -->
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "Container",
    props: ["day", "openedDoors", "link"],
    data() {
        return {
            assetsList: [
                { src: "red.png", alt: "red container" },
                { src: "gray.png", alt: "gray container" },
                { src: "green.png", alt: "green container" },
                { src: "blue.png", alt: "blue container" },
                { src: "yellow.png", alt: "yellow container" }
            ],
            clicked: false,
            opened: false,
            isHovering: false
        };
    },
    watch: {
        clicked() {
            if (this.clicked && this.isCorrectDay) {
                this.opened = true;
                this.$emit("openedDoor", this.day);
            }
        }
    },
    methods: {
        checkForOpened() {
            if (this.openedDoors.includes(parseInt(this.day)))
                this.opened = true;
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
            return this.day <= newDate.getDate() && newDate.getMonth() == 11
                ? true
                : false;
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
        getOpenDoor() {
            return {
                backgroundImage: `url(${require("../assets/container_door_open_" +
                    this.getRandomAssetPath.src)})`
            };
        },
        getContainer() {
            return {
                backgroundImage: `url(${require("../assets/container_" +
                    this.getRandomAssetPath.src)})`
            };
        }
    },
    created() {
        this.checkForOpened();
        console.log(this.link);
    }
};
</script>

<style scoped>
.hovering {
    @apply text-gray-800;
}
</style>
