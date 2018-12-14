<template>
  <div class="home">
    <Cell v-bind:element="element" v-bind:key="element.symbol" v-for="element in elements"/>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import Cell from '@/components/Cell.vue';
import ChemicalElement from '@/ChemicalElement';
import json from '@/elements.json';

@Component({
  components: {
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
