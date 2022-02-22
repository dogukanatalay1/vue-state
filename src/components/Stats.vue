<template>
  <div class="Stats">
    <h1>A different component</h1>
    <p>There are currently {{ countLinks }} links</p>
    <button class="rm" @click="removeAllLinks">Remove All Links</button>
    <p>{{ msg }}</p>
  </div>
</template>

<script>
import { mapGetters, mapMutations, mapActions } from "vuex";

export default {
  name: "StatsVue",
  data() {
    return {
      msg: "",
    };
  },
  computed: {
    ...mapGetters(["countLinks"]),
  },
  methods: {
    ...mapMutations(["REMOVE_ALL"]),
    ...mapActions(["removeAll"]),
    removeAllLinks() {
      this.removeAll().then(() => {
        this.msg = "They have been removed";
      });
    },
  },
};
</script>

<style>
.rm {
  color: #ff0076;
  background: #f9d0e3;
  text-transform: uppercase;
  cursor: pointer;
}
</style>
