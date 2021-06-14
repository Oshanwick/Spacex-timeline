<template>
  <v-timeline-item large>
    <template v-slot:icon>
      <v-avatar> <img :src="launch.links.mission_patch_small" /> </v-avatar>
    </template>
    <template v-slot:opposite>
      <span>{{ launchDate }}</span>
    </template>
    <v-card class="elevation-6">
      <v-card-title class="text-h5">
        Mission: {{ launch.mission_name }}
      </v-card-title>
      <v-card-subtitle>
        Rocket: {{ launch.rocket.rocket_name }}<br />
        Launchsite:{{ launch.launch_site.site_name_long }}
      </v-card-subtitle>
      <v-card-text>{{ launch.details }}</v-card-text>
    </v-card>
  </v-timeline-item>
</template>

<script>
import moment from "moment";
export default {
  props: ["launch"],
  computed: {
    launchDate() {
      return moment(this.launch.lauch_data_local).format("MM/DD/YYYY");
    },
  },
};
</script>