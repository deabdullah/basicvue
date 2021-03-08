<template>
  <q-layout>
    <q-page-container>
      <q-page class="flex flex-center">
        <h1>{{ users }}</h1>
      </q-page>
    </q-page-container>
  </q-layout>
</template>

<script>
import axios from "axios";
export default {
  name: "PageIndex",
  data() {
    return {
      users: null,
    };
  },
  mounted() {
    axios
      .get("https://api.github.com/users")
      .then((response) => (this.users = response));
  },
};
</script>
