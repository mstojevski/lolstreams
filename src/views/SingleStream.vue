<template>
  <VueTwitchPlayer :channel="channel"></VueTwitchPlayer>
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

<style lang="scss" scoped></style>
