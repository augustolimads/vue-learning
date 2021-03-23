<template>
  <div class="w-full flex">
    <div class="m-auto">
      <h1 class="text-3xl font-bold">Heroes List {{ heroesCount }}</h1>
      <ul class="mt-10">
        <li
          v-for="(hero, index) in heroList"
          :key="index"
          class="flex justify-between"
        >
          <span>{{ hero.name }}</span>
          <button @click="removeHero(index)">x</button>
        </li>
      </ul>
      <form @submit.prevent="addHero" class="mt-10">
        <input
          v-model="newHero"
          placeholder="add new hero name"
          class="border rounded"
        />
        <button
          type="submit"
          class="border rounded bg-gradient-to-r from-red-700 to-pink-500 px-3 text-white"
        >
          Add Hero
        </button>
      </form>
    </div>
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
      heroCount: 0,
    };
  },
});
</script>

<style scoped>
</style>
