<template>
  <div>
    <b-card-group deck>
      <b-card
        :footer="username"
        :title="title"
        :img-src="thumbnail"
        img-alt="Image"
        img-top
        tag="article"
        style="max-width: 20rem;"
        class="mb-2"
      >
        <b-card-text>
          Live:{{ viewer_count }}
          <span class="live blink"></span>
        </b-card-text>

        <router-link :to="{ name: 'streams + username' }">
          <b-button variant="primary">Watch Stream</b-button>
        </router-link>
      </b-card>
    </b-card-group>
  </div>
</template>
<script>
export default {
  name: "StreamItem",
  props: {
    id: {
      type: Number
    },
    title: {
      type: String
    },
    thumbnail: {
      type: String
    },
    viewer_count: {
      type: Number
    },
    started_at: {
      type: Date
    },
    username: {
      type: String
    }
  }
};
</script>
<style>
.live {
  display: inline-block;
  width: 15px;
  height: 15px;
  border-radius: 50%;
  background-color: lightgreen;
}

.blink {
  animation: blink-animation 1.5s steps(5, start) infinite;
}
@keyframes blink-animation {
  to {
    visibility: hidden;
  }
}
</style>
