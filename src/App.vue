<template>
  <div id="app">
    <v-app>
      <v-app-bar app color="blue">
        <v-container>
          <v-btn plain :ripple="false" color="white" to="/">Home</v-btn>
          <v-btn plain :ripple="false" color="white" to="/about">About</v-btn>
          <v-spacer></v-spacer>
          <v-btn plain :ripple="false" color="white" to="/add/payment/food?value=200">Food</v-btn>
          <v-btn plain :ripple="false" color="white" to="/add/payment/transport?value=50">Transport</v-btn>
          <v-btn plain :ripple="false" color="white" to="/add/payment/study?value=2000">Study</v-btn>
        </v-container>
      </v-app-bar>
      <v-main>
        <v-container>
          My personal costs
          <router-view :key="$route.fullPath" />
        </v-container>
      </v-main>
    </v-app>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
    };
  },
  methods: {
    show() {
      this.isShown = true;
    },
    hide() {
      this.isShown = false;
      console.log("hide")
    },
  },
  mounted() {
    this.$context.EventEmitter.$on("show", this.show);
    this.$context.EventEmitter.$on("hide", this.hide);
  },
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.nav-costs {
  width: 600px;
  margin: 30px auto;
  display: flex;
  justify-content: space-evenly;

  &.router-link-exact-active {
    color: #42b983;
  }
}
</style>