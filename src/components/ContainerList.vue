<template>
    <div class="w-4/6 pt-64 mx-auto">
        <div class="flex flex-row flex-wrap-reverse mx-auto">
            <Container
                v-for="(item, i) in grid.toString().split(',')"
                :key="i"
                :day="item"
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
                [0, 0, 17, 22],
                [21, 0, 25, 0],
                [0, 6, 15, 0],
                [7, 18, 0, 23]
            ]
        };
    },
    watch: {
        openedDoors() {
            let uniqueDoorNums = this.openedDoors.filter(
                (v, i, arr) => arr.indexOf(v) === i
            );
            document.cookie = `openedDoors=${uniqueDoorNums.toString()}`;
        }
    },
    methods: {
        createCookie() {
            if (!document.cookie) {
                document.cookie = "openedDoors=0";
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
        }
    },
    created() {
        this.createCookie();
        this.setOpenedDoors();
    }
};
</script>

<style></style>
