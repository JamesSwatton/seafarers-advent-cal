<template>
    <div class="relative w-5/6 pl-3 mx-auto mb-8 md:mb-12 md:pl-0 md:w-4/6">
        <div class="flex flex-row flex-wrap-reverse mx-auto">
            <Container
                v-for="(item, i) in grid.toString().split(',')"
                :key="i"
                :day="item"
                :link="getLink(item)"
                :openedDoors="openedDoors"
                @openedDoor="openedDoors.push(parseInt($event))"
            ></Container>
        </div>
    </div>
</template>

<script>
import Container from "./Container";
export default {
    name: "ContainerList",
    components: { Container },
    data() {
        return {
            openedDoors: [],
            grid: [
                [11, 0, 3, 0],
                [0, 4, 0, 16],
                [0, 20, 14, 0],
                [24, 8, 0, 0],
                [0, 5, 0, 2],
                [0, 12, 0, 19],
                [10, 1, 13, 0],
                [9, 0, 17, 22],
                [21, 0, 25, 0],
                [0, 6, 15, 0],
                [7, 18, 0, 23]
            ],
            links: {
                "1":
                    "https://www.seafarerswelfare.org/festive-countdown-day-1-giveaway",
                "2":
                    "https://www.seafarerswelfare.org/festive-countdown-day-2-decorations",
                "3":
                    "https://www.seafarerswelfare.org/festive-countdown-day-3-party-game-1",
                "4":
                    "https://www.seafarerswelfare.org/festive-countdown-day-4-fancy-dress",
                "5":
                    "https://www.seafarerswelfare.org/festive-countdown-day-5-recipes-1",
                "6":
                    "https://www.seafarerswelfare.org/festive-countdown-day-6-message-board",
                "7":
                    "https://www.seafarerswelfare.org/assets/documents/resources/SHS-Question-Day-7.pdf",
                "8":
                    "https://www.seafarerswelfare.org/festive-countdown-day-8-giveaway",
                "9":
                    "https://www.seafarerswelfare.org/festive-countdown-day-9-party-game-2",
                "10":
                    "https://www.seafarerswelfare.org/festive-countdown-day-10-recipes-2",
                "11":
                    "https://www.seafarerswelfare.org/assets/documents/resources/SHS-Answer-Day-11.pdf",
                "12": "https://landing.kvh.com/FestiveCountdown",
                "13":
                    "https://www.seafarerswelfare.org/festive-countdown-day-13-workout",
                "14":
                    "https://www.seafarerswelfare.org/festive-countdown-day-14-party-game-3",
                "15": "https://www.youtube.com/embed/6QishjbYrzI",
                "16":
                    "https://www.seafarerswelfare.org/festive-countdown-day-16-recipes-3",
                "17":
                    "https://www.seafarerswelfare.org/festive-countdown-day-17-news-from-home",
                "18":
                    "https://www.seafarerswelfare.org/festive-countdown-day-18-party-game-4",
                "19":
                    "https://www.seafarerswelfare.org/festive-countdown-day-19-free-calls-and-minutes",
                "20":
                    "https://www.seafarerswelfare.org/festive-countdown-day-20-icma-videos",
                "21": "https://www.youtube.com/embed/oEkV1bu8XbQ",
                "22":
                    "https://www.seafarerswelfare.org/festive-countdown-day-22-recipes-4",
                "23":
                    "https://www.seafarerswelfare.org/festive-countdown-day-23-free-calls-and-minutes",
                "24":
                    "https://www.seafarerswelfare.org/festive-countdown-day-24-party-game-5",
                "25": "https://www.youtube.com/embed/HLBaoir1d3o"
            }
        };
    },
    watch: {
        openedDoors() {
            let uniqueDoorNums = this.openedDoors.filter(
                (v, i, arr) => arr.indexOf(v) === i
            );
            document.cookie = `openedDoors=${uniqueDoorNums.toString()}`;
            console.log(document.cookie);
        }
    },
    methods: {
        createCookie() {
            if (!document.cookie) {
                document.cookie = "openedDoors=";
                console.log(document.cookie);
            } else {
                console.log(document.cookie);
            }
        },
        setOpenedDoors() {
            let crumbs = document.cookie.split("; ");
            crumbs.forEach(crumb => {
                let cSplit = crumb.split("=");
                if (cSplit[0] == "openedDoors") {
                    this.openedDoors = cSplit[1]
                        .split(",")
                        .map(n => parseInt(n));
                }
            });
        },
        getLink(key) {
            return this.links[key]
                ? this.links[key]
                : "https://www.seafarerswelfare.org/";
        }
    },
    created() {
        this.createCookie();
        this.setOpenedDoors();
    }
};
</script>

<style></style>
