<template>
  <VueTwitchPlayer
    width="100%"
    height="600"
    :channel="channel"
  ></VueTwitchPlayer>
</template>

<script>
import VueTwitchPlayer from "vue-twitch-player";

export default {
  components: {
    VueTwitchPlayer
  },
  data() {
    return {
      channel: this.$route.params.channel
    };
  }
};
</script>
