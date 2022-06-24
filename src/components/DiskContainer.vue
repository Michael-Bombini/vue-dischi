<template>
    <main class="flex-grow-1">
        <div class="container">
            <div class="row row-cols-5 g-4">
                <div class="col" v-for="disk in diskList" :key="disk.title">
                    <TheDisk :info="disk"/>
                </div>
           </div>
        </div>
    </main>
</template>

<script>
import axios from "axios";
import TheDisk from "./TheDisk.vue";


    export default {
    name: "DiskContainer",
    data() {
        return {
            diskList: [],
        };
    },
    methods: {
        fetchDisk() {
            axios.get("https://flynn.boolean.careers/exercises/api/array/music")
                .then((response) => {
                this.diskList = response.data.response;
            });
        }
    },
    mounted() {
        this.fetchDisk();
    },
    components: { TheDisk }
}
</script>

<style lang="scss" scoped>
main {
    background-color: #1E2D3B;
    height: 90vh;
    padding: 7rem 0;
}
</style>