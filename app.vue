<template>
  <main>
    <header>
      <h1>Music</h1>
    </header>
    <div class="music-container" v-if="data">
      <MusicCard :data="data" />
    </div>
    <p v-else>something went wrong!</p>
  </main>
</template>

<script setup>
const query = groq`*[_type == "music"]{
  name,description,date, link
}`;
const { data } = useSanityQuery(query);
if (data) console.log(data);
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Lora:ital@0;1&display=swap");
html {
  background: #f5f4ed;
}
main {
  display: flex;
  flex-direction: column;
  align-items: center;
  height: 100vh;
  width: 100vw;
  margin-top: -0.5em;
  margin-left: -0.5em;
  background: #f5f4ed;
  font-family: Lora, serif;
  overflow: hidden;
  .music-container {
    display: flex;
    flex-direction: row;
    justify-content: space-around;
    width: 90%;
  }
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
    border-bottom: 1px solid;
    height: 10em;
    display: flex;
    justify-content: center;
    align-items: center;
    h1 {
      font-size: 36px;
      font-style: normal;
      font-weight: 400;
      letter-spacing: 0;
      line-height: 1.38;
    }
  }
}
</style>
