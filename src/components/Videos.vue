<template>
    <v-card class="mx-auto" max-width="400" tile>
        <v-toolbar dark>
            <v-toolbar-title>Videos</v-toolbar-title>
        </v-toolbar>
        <v-container>
            <v-row>
                <v-col>
                    <v-list>
                        <v-list-item-group is="transition-group" name="neo-list">
                            <v-list-item v-for="(video, index) in videos" :key="index" :class="{'shadow-sm': true}">
                                <v-list-item-content>
                                    <v-list-item-title>{{video.title}}</v-list-item-title>
                                </v-list-item-content>
                                <v-btn @click="remove(index)">remove</v-btn>
                            </v-list-item>
                        </v-list-item-group>
                    </v-list>
                </v-col>
            </v-row>
        </v-container>
    </v-card>
</template>

<script>
    import axios from "axios";

    export default {
        data() {
            return {
                videos: []
            };
        },
        created: function () {
            this.$root.$on('authorized', () => {
                axios.get("/videos").then(response => {
                    this.videos = response.data.data;
                });
            });
        },
        methods: {
            remove: function (index) {
                this.videos.splice(index, 1);
            }
        }
    };
</script>

<style scoped>
    .neo-list-leave-to, .neo-list-enter {
        opacity: 0;
        transform: translateY(30px);
    }

    .neo-list-enter-active, .neo-list-leave-active {
        transition: all 1s linear;
    }
</style>