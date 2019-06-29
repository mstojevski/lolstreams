<template>
  <div class="Home">
    <b-container class="bv-example-row">
      <b-row class="row">
        <b-col md="4" sm="12" v-for="stream in streams" :key="stream.id">
          <StreamItem
            :username="stream.user_name"
            :title="stream.title"
            :viewer_count="stream.viewer_count"
            :thumbnail="stream.thumbnail_url"
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
      .then(jsonData => {
        for (let stream in jsonData.data) {
          const regex = /\{(.*?)\}/g;
          // Matching witdh and height

          let thumbnail = jsonData.data[stream].thumbnail_url;
          const width = regex.exec(thumbnail);
          const height = regex.exec(thumbnail);

          jsonData.data[stream].thumbnail_url = jsonData.data[
            stream
          ].thumbnail_url.replace(width[0], 320);
          jsonData.data[stream].thumbnail_url = jsonData.data[
            stream
          ].thumbnail_url.replace(height[0], 180);

          this.streams = jsonData.data;
        }
        return this.streams;
      });
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
@media (max-width: 768px) {
  .Home {
    padding: 25px;
  }
}
</style>
