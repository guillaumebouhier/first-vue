<template>
  <v-app>
    <v-content>
      <HelloWorld v-bind:store="store" />
    </v-content>
  </v-app>
</template>

<script>
import HelloWorld from "./components/HelloWorld";

import Vuex from "vuex";
import Vue from "vue";
Vue.use(Vuex);

const Store = new Vuex.Store({
  state: {
    count: 0,
    racks: []
  },
  mutations: {
    increment(state) {
      state.count++;
    },
    addRack(state, rack) {
      state.racks.push(rack);
    },
    toggleRack(state, rack) {
      rack.activated = !rack.activated;
    }
  },
  getters: {
    racks: state => {
      return state.racks;
    }
  }
});

Store.commit("addRack", {
  brand: "furman",
  imgUrl: "racks/furman.png",
  activated: true
});
Store.commit("addRack", {
  brand: "engl",
  imgUrl: "racks/engl-e530.png",
  activated: true
});
Store.commit("addRack", {
  brand: "fractal",
  imgUrl: "racks/axefx2.png",
  activated: false
});
Store.commit("addRack", {
  brand: "rocktron",
  imgUrl: "racks/rocktron-velocity.png",
  activated: true
});

export default {
  name: "App",
  components: {
    HelloWorld
  },
  data: () => ({
    store: Store
  })
};
</script>
