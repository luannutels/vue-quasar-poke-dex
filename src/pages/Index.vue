<template>
  <q-page class="flex flex-center">
    <q-img :src="url" :ratio="1" />
    <h1>{{ name }}</h1>
  </q-page>
</template>

<script>
import api from "../services/api";
export default {
  name: "PageIndex",

  data() {
    return {
      name: "",
      url: "",
    };
  },

  beforeMount() {
    api
      .get("/pokemon/2/")
      .then((response) => {
        // handle success
        console.log(response);
        this.name = response.data.name;
        this.url = response.data.sprites.other.dream_world.front_default;
      })
      .catch((error) => {
        // handle error
        console.log(error);
      })
      .then(() => {
        // always executed
      });
  },
};
</script>
