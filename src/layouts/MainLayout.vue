<template>
  <q-layout view="lHh Lpr lFf">
    <!-- <q-header elevated> </q-header> -->

    <Header />
    <q-page-container>
      <router-view />
    </q-page-container>
    <Footer />
  </q-layout>
</template>

<script>
import Header from "../components/Header.vue";
import Footer from "../components/Footer.vue";
export default {
  name: "MainLayout",
  components: { Header, Footer },
  data() {
    return {
      leftDrawerOpen: false,
    };
  },
};
</script>
