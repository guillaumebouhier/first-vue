<template>
  <v-app>
    <v-main>
      <HelloWorld :store="store" :library="library" />
    </v-main>
  </v-app>
</template>

<script>
import HelloWorld from './components/HelloWorld';

import Vuex from 'vuex';
import Vue from 'vue';
Vue.use(Vuex);

const Store = new Vuex.Store({
  state: {
    count: 0,
    racks: [],
    activated: false,
  },
  mutations: {
    increment(state) {
      state.count++;
    },
    addRack(state, rack) {
      state.racks.push({ ...rack });
    },
    deleteRack(state, rack) {
      state.racks.splice(rack, 1);
    },
    toggleRack(state, rack) {
      rack.activated = !rack.activated;
    },
    activateRack(state, rack) {
      rack.activated = true;
    },
  },
  getters: {
    racks: (state) => {
      return state.racks;
    },
  },
});

const Library = new Vuex.Store({
  state: {
    count: 0,
    racks: [],
    activated: false,
  },
  mutations: {
    addRack(state, rack) {
      state.racks.push(rack);
    },
  },
  getters: {
    racks: (state) => {
      return state.racks;
    },
  },
});

Library.commit('addRack', {
  brand: 'furman',
  model: 'PL8-C',
  imgUrl: 'racks/furman.png',
  activated: true,
});
Library.commit('addRack', {
  brand: 'engl',
  model: 'e530 Modern Rock',
  imgUrl: 'racks/engl-e530.png',
  activated: true,
});
Library.commit('addRack', {
  brand: 'fractal audio',
  model: 'Axe Fx 2 XL+',
  imgUrl: 'racks/axefx2.png',
  activated: false,
});
Library.commit('addRack', {
  brand: 'rocktron',
  model: 'velocity 300',
  imgUrl: 'racks/rocktron-velocity.png',
  activated: true,
});
Library.commit('addRack', {
  brand: 'kemper',
  model: 'Kemper Profiler',
  imgUrl: 'racks/kemper.png',
  activated: true,
});

Store.commit('addRack', Library.getters.racks[0]);
Store.commit('activateRack', Store.getters.racks[0]);

Store.commit('addRack', Library.getters.racks[1]);
Store.commit('activateRack', Store.getters.racks[1]);

Store.commit('addRack', Library.getters.racks[2]);
Store.commit('activateRack', Store.getters.racks[2]);

Store.commit('addRack', Library.getters.racks[3]);
Store.commit('activateRack', Store.getters.racks[3]);

export default {
  name: 'App',
  components: {
    HelloWorld,
  },
  data: () => ({
    store: Store,
    library: Library,
  }),
};
</script>
