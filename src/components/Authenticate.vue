<template>
  <v-container>
    <v-card class="mx-auto" max-width="400">
      <v-form>
        <v-toolbar dark>
          <v-toolbar-title>Authenticate</v-toolbar-title>
        </v-toolbar>
        <v-row>
          <v-col cols="12" sm="4" offset-sm="1">
            <v-text-field v-model="apiKey" label="API Key" required></v-text-field>
            <v-btn class="mr-4" @click="submit">submit</v-btn>
          </v-col>
        </v-row>
      </v-form>
    </v-card>
  </v-container>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      apiKey: "",
      accessToken: "",
      refreshToken: ""
    };
  },
  methods: {
    submit: function() {
      axios
        .post("https://sandbox.api.video/auth/api-key", {
          apiKey: this.apiKey
        })
        .then(response => {
          this.accessToken = response.data.access_token;
          this.refreshToken = response.data.refresh_token;
        });
    }
  }
};
</script>