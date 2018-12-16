<template>
  <table class="home">
    <tr>
      <td v-for="n in 18" v-bind:key="'group'+n" class="group">{{ n }}</td>
    </tr>
    <template v-for="(element, index) in elements">
      <tr v-bind:key="index">
        <Cell v-bind:element="element" v-bind:key="element.symbol"/>
        <template v-if="element.number === 1">
          <td class="empty"></td>
          <td class="empty" colspan="7" rowspan="3"></td>
          <td class="empty" colspan="3" rowspan="3"></td>
          <td class="empty" colspan="5"></td>
        </template>
      </tr>
      <tr v-if="element.number === 118 || element.number === 71" v-bind:key="'emptyAfter'+element.number">
        <td colspan="18" class="empty"></td>
      </tr>
    </template>
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
