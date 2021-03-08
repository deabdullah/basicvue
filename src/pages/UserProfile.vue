<template>
  <div class="q-pa-md" v-if="user">
    <div class="q-gutter-md row items-start justify-center">
      <q-img
        :src="user.avatar_url"
        style="max-width: 400px; height: 200px"
        contain
      >
        <div class="absolute-bottom text-subtitle1 text-center">
          {{ $route.params.login }}
        </div>
      </q-img>
    </div>
    <div class="q-gutter-md row items-start justify-center">
      <p>
        Type: <strong>{{ user.type }}</strong>
      </p>
    </div>
    <div class="q-gutter-md row items-start justify-center">
      <p>
        Repository: <strong>{{ user.public_repos }}</strong>
      </p>
    </div>
    <div class="q-gutter-md row items-start justify-center">
      <p>
        Followers: <strong>{{ user.followers }}</strong>
      </p>
    </div>
    <div class="q-gutter-md row items-start justify-center">
      <q-btn :to="user.url" label="To Github Profile" outline color="purple" />
    </div>
  </div>
</template>
<script>
import axios from "axios";
export default {
  name: "UserProfile",
  data() {
    return {
      user: null,
    };
  },

  mounted() {
    axios
      .get("https://api.github.com/users/" + this.$route.params.login)
      .then((response) => (this.user = response.data));
  },
};
</script>