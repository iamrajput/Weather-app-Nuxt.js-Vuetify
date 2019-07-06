<template>
  <v-app>
    <v-toolbar color="#C0CA33" dark>
      <!-- <v-toolbar-side-icon></v-toolbar-side-icon> -->
      <v-toolbar-title><n-link to="/">VueGram</n-link></v-toolbar-title>
      <v-spacer></v-spacer>
      <v-toolbar-items class="hidden-sm-and-down">
        <v-btn flat>
          <n-link to="/weather-app">Weather app</n-link>
        </v-btn>
        <!-- <v-btn flat>
          <n-link to="/about">About</n-link>
        </v-btn>
        <v-btn flat>
          <n-link to="/me">Me</n-link>
        </v-btn> -->
      </v-toolbar-items>
    </v-toolbar>
    <nuxt/>
    <!-- <v-footer :fixed="fixed" app>
      <span>&copy; 2019</span>
    </v-footer> -->
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      clipped: false,
      drawer: false,
      fixed: false,
      items: [
        {
          icon: "apps",
          title: "Welcome",
          to: "/"
        },
        {
          icon: "bubble_chart",
          title: "Inspire",
          to: "/inspire"
        }
      ],
      miniVariant: false,
      right: true,
      rightDrawer: false,
      title: "Vuetify.js"
    };
  }
};
</script>
<style>
a{
  text-decoration:none;
  color: white;
}
</style>
