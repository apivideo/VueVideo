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
            <Videos v-cloak v-if="false"/>
        </v-content>
    </v-app>
</template>

<script>
    import Videos from './components/Videos';
    import Authenticate from './components/Authenticate';

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
