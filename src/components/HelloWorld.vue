<template>
  <div class="hello">
    <div class="left">
      <h1>{{ title }}</h1>

      <form @submit.prevent="addLink">
        <input
          class="input"
          type="text"
          placeholder="Add a link"
          v-model="newLink"
        />
      </form>
      <ul>
        <li v-for="(link, index) in links" :key="index">
          {{ link }}
          <button @click="removeLinks(index)" class="rm">Remove</button>
        </li>
      </ul>
    </div>
    <div class="right">
      <Stats />
    </div>
  </div>
</template>

<script>
import { mapState, mapMutations, mapActions } from "vuex";
import Stats from "../components/Stats.vue";

export default {
  name: "HelloWorld",
  data() {
    return {
      newLink: "",
    };
  },
  components: {
    Stats,
  },
  computed: {
    ...mapState(["title", "links"]),
  },
  methods: {
    ...mapMutations(["ADD_LINK"]),
    ...mapActions(["removeLink"]),
    addLink: function () {
      this.ADD_LINK(this.newLink);
      this.newLink = "";
    },
    removeLinks: function (link) {
      this.removeLink(link);
    },
  },
};
</script>

<style>
.input {
  border: 0.5px solid gray;
  padding: 20px;
  width: calc(100% - 40px);
  box-shadow: 0 5px 5px lightgrey;
  margin-bottom: 50px;
  outline: none;
}
.rm {
  color: #ff0076;
  background: #f9d0e3;
  text-transform: uppercase;
  cursor: pointer;
}
</style>
