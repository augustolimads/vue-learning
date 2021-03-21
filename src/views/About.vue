<template>
  <main class="render">
    <div>
      <h1>Essa é a página onde eu estudo {{ type }}</h1>
    </div>
    <hr />

    <div>
      <span v-bind:title="message">
        Pare o mouse sobre mim e veja a dica interligada dinamicamente!
      </span>
    </div>
    <hr />

    <div>
      <p v-if="seen">Agora você me viu</p>
    </div>
    <hr />

    <div>
      <ol>
        <li v-for="todo in todos" v-bind:key="todo.text">
          {{ todo.text }}
        </li>
      </ol>
    </div>
    <hr />

    <div>
      <p>{{ reverse }}</p>
      <button v-on:click="reverseMsg">Inverter Mensagem</button>
    </div>
    <hr />

    <div>
      <p v-if="inputMsg <= 0">Digite uma mensagem</p>
      <p>{{ inputMsg }}</p>
      <input v-model="inputMsg" />
    </div>
    <hr />

    <ComponentChildren></ComponentChildren>
  </main>
</template>

<script lang="ts">
import ComponentChildren from "@/components/ComponentChildren.vue";
import Vue from "vue";

export default Vue.extend({
  components: { ComponentChildren },
  name: "render",
  data() {
    return {
      type: "Vue",
      message: `Você carregou esta página em ${new Date().toLocaleString()}`,
      seen: true,
      todos: [
        { text: "Aprender JavaScript" },
        { text: "Aprender Vue" },
        { text: "Criar algo incrível" },
      ],
      reverse: "Olá Vue!!!",
      inputMsg: "Hello Vue!!!",
    };
  },
  methods: {
    reverseMsg() {
      this.reverse = this.reverse.split("").reverse().join("");
    },
  },
});
</script>
