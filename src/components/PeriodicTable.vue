<template>
  <table class="home">
    <tr>
      <td v-for="n in 18" v-bind:key="'group'+n" class="group">{{ n }}</td>
    </tr>
    <template v-for="(row, index) in rows">
      <tr v-bind:key="index">
        <template v-for="element in row">
          <Cell v-bind:element="element" v-bind:key="element.symbol"/>
          <template v-if="element.number === 1">
            <td class="empty" v-bind:key="'emptyAfter'+element.number"></td>
            <td class="empty" colspan="7" rowspan="3" v-bind:key="'emptyAfter'+element.number"></td>
            <td class="empty" colspan="3" rowspan="3" v-bind:key="'emptyAfter'+element.number"></td>
            <td class="empty" colspan="5" v-bind:key="'emptyAfter'+element.number"></td>
          </template>
        </template>
      </tr>
      <tr v-if="index === 7 || index === 8" v-bind:key="'emptyAfter'+index">
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
  private rows: ChemicalElement[][];
  constructor() {
    super();
    const left = new Set([1, 3, 11, 19, 37, 55, 87, 58, 90]);
    function splitToRows(total: ChemicalElement[][], current: ChemicalElement) {
      if (left.has(current.number)) {
        total.push([current]);
      } else {
        total[total.length - 1].push(current);
      }
      return total;
    }
    this.rows = json.reduce(splitToRows, []);
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
