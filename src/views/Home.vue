<template>
  <div class="home">
    <Cell v-bind:element="element" v-bind:key="element.symbol" v-for="element in elements"/>
    <img alt="Vue logo" src="../assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js + TypeScript App"/>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import HelloWorld from '@/components/HelloWorld.vue'; // @ is an alias to /src
import Cell from '@/components/Cell.vue';
import ChemicalElement from '@/ChemicalElement';
import json from '@/elements.json';

@Component({
  components: {
    HelloWorld,
    Cell,
  },
})
export default class Home extends Vue {
  private elements: ChemicalElement[];
  constructor() {
    super();
    this.elements = json;
  }
}
</script>
