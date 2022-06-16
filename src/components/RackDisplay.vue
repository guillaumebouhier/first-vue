<template>
  <v-app id="inspire">
    <div
      v-for="(rack, idx) of store.getters.racks"
      :key="idx"
      class="rack-container"
    >
      <img
        @click="store.commit('toggleRack', rack)"
        :src="rackImage(rack.imgUrl)"
        :class="{ disabled: !rack.activated }"
      />
      <v-btn
        elevation="2"
        icon
        x-small
        class="delete-button"
        @click="store.commit('deleteRack', idx)"
      >
        <v-icon dark>
          mdi-minus
        </v-icon></v-btn
      >
    </div>
  </v-app>
</template>

<script>
export default {
  props: { store: Object },

  methods: {
    rackImage(imgUrl) {
      return require('@/assets/' + imgUrl);
    },
  },
};
</script>

<style lang="css">
.delete-button {
  background-color: grey;
  margin-left: 8px;
}
.rack-container {
  display: flex;
  justify-content: center;
  padding: 10px;
  opacity: 1;
}
.disabled {
  opacity: 0.2;
}
</style>
