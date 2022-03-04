<template>
  <q-page class="flex flex-center"> </q-page>
</template>

<script>
import api from "../services/api";
export default {
  name: "PageIndex",

  beforeMount() {
    api
      .get("/pokemon/2/")
      .then((response) => {
        // handle success
        console.log(response);
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
