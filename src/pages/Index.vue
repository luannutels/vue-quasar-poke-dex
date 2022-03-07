<template>
  <q-page class="flex flex-center">
    <h2>{{ name }}</h2>
    <q-img :src="url" :ratio="1" width="250px" />
    <div class="row justify-around full-width">
      <q-input filled v-model="id" />
      <q-btn color="purple" label="Pesquisar" />
    </div>
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
      id: "1",
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
