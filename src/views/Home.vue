<template>
  <div class="Home">
    <b-container class="bv-example-row">
      <b-row class="row">
        <b-col cols="4" v-for="stream in streams" :key="stream.id">
          <StreamItem
            :username="stream.user_name"
            :title="stream.title"
            :viewer_count="stream.viewer_count"
          />
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
import StreamItem from "@/components/StreamItem.vue";
export default {
  name: "home",
  components: {
    StreamItem
  },
  data() {
    return {
      streams: []
    };
  },
  created() {
    fetch("https://api.twitch.tv/helix/streams?game_id=21779", {
      headers: {
        "Client-ID": "sl3e7mshstysne2dhw44pa1e95ihtn"
      }
    })
      .then(response => response.json())
      // .then(data => console.log(data))
      .then(blob => (this.streams = blob.data));
  }
};
</script>

<style scoped>
.Home {
  padding: 30px 0;
}
.row.display-flex {
  display: flex;
  flex-wrap: wrap;
}
.row.display-flex > [class*="col-"] {
  display: flex;
  flex-direction: column;
}
</style>
