<template>
    <v-card class="mx-auto" max-width="400" tile>
        <v-toolbar dark>
            <v-toolbar-title>Videos</v-toolbar-title>
        </v-toolbar>
        <v-container>
            <v-row>
                <v-col>
                    <v-list>
                        <v-list-item-group>
                            <v-list-item v-for="(video, index) in videos" :key="index">
                                <v-list-item-content>
                                    <v-list-item-title v-html="video">{{video.title}}</v-list-item-title>
                                </v-list-item-content>
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
            // eslint-disable-next-line no-global-assign
            self = this;
            this.$root.$on('authorized', function () {
                axios.get("/videos").then(function (response) {
                    self.videos = response.data.data;
                });
            });
        }
    };
</script>