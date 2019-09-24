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

const store = new Vuex.Store({
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
    }
  },
  getters: {
    racks: state => {
      return state.racks;
    },
    rackImage: state => id => {
      return require("@/assets/" + state.racks[id].imgUrl);
    }
  }
});

store.commit("addRack", {
  brand: "furman",
  imgUrl: "racks/furman.png"
});
store.commit("addRack", {
  brand: "engl",
  imgUrl: "racks/engle530.png"
});

export default {
  name: "App",
  components: {
    HelloWorld
  },
  data: () => ({
    store: store
  })
};
</script>
