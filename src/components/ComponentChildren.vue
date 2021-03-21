<template>
  <div class="compo">Sou um component {{compo}}</div>
</template>

<script lang="ts">
import Vue from "vue";

export default Vue.extend({
  name: "compo",
  data() {
    return {
      compo: "irado!",

    };
  },
});
</script>
