<template>
  <div v-for="music in props.data" class="music-post">
    <p>{{ music.name }}</p>
    <p>{{ music.description }}</p>
    <p>{{ dayjs(music.date).format("MM/DD/YY") }}</p>
    <iframe
      style="border-radius: 12px"
      :src="`https://open.spotify.com/embed/playlist/${
        music.link.split('https://open.spotify.com/playlist/')[1]
      }?utm_source=generator`"
      width="100%"
      height="352"
      frameBorder="0"
      allowfullscreen=""
      allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture"
      loading="lazy"
    ></iframe>
  </div>
</template>

<script setup>
import dayjs from "dayjs";
const props = defineProps(["data"]);
</script>
