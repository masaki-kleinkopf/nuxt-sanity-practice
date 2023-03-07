<template class="app">
  <main>
    <header>
      <h1>Music</h1>
    </header>
    <div class="music-container" v-if="data" v-for="music in data">
      <p>{{ music.name }}</p>

      <p>{{ music.description }}</p>

      <iframe
        style="border-radius: 12px"
        :src="music.link"
        width="100%"
        height="352"
        frameBorder="0"
        allowfullscreen=""
        allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture"
        loading="lazy"
      ></iframe>
    </div>
    <p v-else>something went wrong!</p>
  </main>
</template>

<script setup>
const query = groq`*[_type == "music"]{
  name,description,link
}`;
const { data } = useSanityQuery(query);
if (data) console.log(data);
</script>

<style scoped lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Lora:ital@0;1&display=swap");

main {
  display: flex;
  flex-direction: column;
  align-items: center;
  height: 100vh;
  width: 100vw;
  margin-top: -0.5em;
  margin-left: -0.5em;
  background-color: #f5f4ed;
  font-family: Lora, serif;
  p {
    display: flex;
    justify-content: center;
    font-style: italic;
    font-weight: 400;
    letter-spacing: 0;
    line-height: 1.5;
  }
  header {
    width: 100%;
    border-bottom: solid;
    font-size: 36px;
    font-style: normal;
    font-weight: 400;
    letter-spacing: 0;
    line-height: 1.38;
    height: 4em;
    display: flex;
    justify-content: center;
    align-items: center;
    h1 {
      font-size: 2em;
    }
  }
}
</style>
