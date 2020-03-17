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
                            <v-list-item v-for="(message, i) in messages" :key="i">
                                <v-list-item-content>
                                    <v-list-item-title v-html="message"></v-list-item-title>
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
                messages: []
            };
        },
        created: function () {
          // eslint-disable-next-line no-global-assign
            self = this;
            axios.get("http://localhost:3000/messages").then(function (response) {
                self.messages = response.data;
            });
        }
    };
</script>