<template>
  <div>
    <h1>Heroes List {{ heroesCount }}</h1>
    <ul>
      <li v-for="(hero, index) in heroList" :key="index">
        <span>{{ hero.name }}</span>
        <button @click="removeHero(index)">x</button>
      </li>
    </ul>
    <form @submit.prevent="addHero">
      <input v-model="newHero" placeholder="add new hero name" />
      <button type="submit">Add Hero</button>
    </form>
  </div>
</template>

<script lang="ts">
import Vue from "vue";

export default Vue.extend({
  computed: {
    heroesCount() {
      return this.heroList.length;
    },
  },
  methods: {
    addHero() {
      if (this.newHero !== "") {
        this.heroList.push({ name: this.newHero });
        this.newHero = "";
      }
    },
    removeHero(index: number) {
      this.heroList = this.heroList.filter((el, i) => i !== index);
    },
  },
  data() {
    return {
      newHero: "",
      heroList: [{ name: "Superman" }],
    };
  },
});
</script>

<style scoped>
</style>
