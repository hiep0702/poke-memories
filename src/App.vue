<template>
  <main-screen
    v-if="statusMatch === 'default'"
    @onStart="onHandleBeforeStart($event)"
  />
  <interact-screen v-if="statusMatch === 'match'" />
</template>

<script>
import InteractScreen from "./components/InteractScreen.vue";
import MainScreen from "./components/MainScreen.vue";

export default {
  name: "App",
  data() {
    return {
      statusMatch: "default",
    };
  },
  components: {
    MainScreen,
    InteractScreen,
  },
  methods: {
    onHandleBeforeStart(config) {
      console.log("run onHandleBeforeStart, ", config);
      this.statusMatch = "match";
    },
  },
};
</script>
