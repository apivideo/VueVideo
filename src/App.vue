<template>
    <v-app>
        <v-app-bar
                app
                color="primary"
                dark
        >

        </v-app-bar>

        <v-content>
            <br>
            <Authenticate/>
            <br>
            <Videos v-cloak v-if="true"/>
        </v-content>
    </v-app>
</template>

<script>
    import Videos from './components/Videos';
    import Authenticate from './components/Authenticate';
    import axios from "axios";

    axios.defaults.baseURL = 'https://sandbox.api.video';

    export default {
        name: 'App',

        components: {
            Videos,
            Authenticate
        },

        data: () => ({
            //
        }),
    };
</script>

<style>
    [v-cloak] {
        display: none;
    }
</style>
