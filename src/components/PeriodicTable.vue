<template>
  <table class="home">
    <tr>
      <td v-for="n in 18" v-bind:key="('group'+n)" class="group">{{ n }}</td>
    </tr>
    <tr>
      <Cell v-bind:element="element" v-bind:key="element.symbol" v-for="element in elements"/>
    </tr>
  </table>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import Cell from './Cell.vue';
import ChemicalElement from '@/ChemicalElement';
import json from '@/elements.json';

@Component({
  components: {
    Cell,
  },
})
export default class PeriodicTable extends Vue {
  private elements: ChemicalElement[];
  constructor() {
    super();
    this.elements = json;
  }
}
</script>
<style lang="stylus" scoped>
table
  border-collapse collapse
  width 100%
  margin-bottom 20px

.group
  padding-top 5px
  padding-bottom 5px

.empty
  border none
</style>
