<template>
  <v-app>
    <v-app-bar app color="deep-purple accent-2" dark>
      <div class="d-flex align-center">
        <h2>Spacex Timeline</h2>
      </div>

      <v-spacer></v-spacer>
    </v-app-bar>
    <v-content>
      <v-container>
        <v-timeline v-if="launches.length > 0">
          <Lauchtimelineitem
            v-for="launch in launches"
            :key="launch.flight_number"
            :launch="launch"
          />
        </v-timeline>
      </v-container>
    </v-content>
    <v-main> </v-main>
  </v-app>
</template>

<script>
import axios from "axios";
import Lauchtimelineitem from "./components/Launchtimelineitem.vue";
export default {
  name: "App",

  components: {
    Lauchtimelineitem,
  },

  data: () => ({
    launches: [],
  }),
  async created() {
    const { data } = await axios.get("https://api.spacexdata.com/v3/launches");

    data.forEach((launch) => {
      this.launches.push(launch);
    });
    console.log(this.launches);
  },
};
</script>
