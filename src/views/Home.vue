<template>
  <div class="home">
    <Cell v-bind:element="element" />
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
  private element: ChemicalElement;
  constructor() {
    super();
    this.element = json[0];
  }
}
</script>
