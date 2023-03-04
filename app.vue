<template class="app">
  <header>
    <h1>First Sanity/Nuxt site</h1>
  </header>
  <main>
    <li v-if="data">
      <ul
        v-for="pet in data"
      >
        <p>name:{{ pet.name }}</p>

        <p>description:{{ pet.description }}</p>

        <img :src="pet.imageUrl"/>
        <button @click="handleClick">click me</button>
      </ul>
      </li>
    <p v-else>something went wrong!</p>
  </main>
</template>

<script setup>
const query = groq`*[_type == "pet"]{
  name,description,"imageUrl": image.asset->url
}`;
const { data } = useSanityQuery(query);
data && console.log(data);

const handleClick = (event) => {
  event.preventDefault
  console.log(event)
}
</script>

<style module lang="scss">
header {
  display: flex;
  justify-content: center;
}
main {
  display: flex;
  justify-content: center;
  li {
    list-style-type: none;
  }
}
</style>
