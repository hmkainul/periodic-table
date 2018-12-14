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

const hydrogen = {
  number: 1,
  symbol: 'H',
  name: 'Hydrogen',
  weight: '1.008',
};
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
    this.element = hydrogen;
  }
}
</script>
