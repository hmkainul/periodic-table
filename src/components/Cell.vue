<template>
  <td class="element" v-on:click="click" v-on:mousedown="mousedown" v-bind:class="element.type" v-bind:id="element.symbol">
    <span class="number">{{ element.number }}<br></span>
    <span class="symbol">{{ element.symbol }}<br></span>
    <span class="name">{{ element.name }}<br></span>
    <span class="weight">{{ element.weight }}</span>
  </td>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';
import ChemicalElement from '@/ChemicalElement.ts';

@Component
export default class Cell extends Vue {
  @Prop() private element!: ChemicalElement;
  private click(event: Event) {
    console.log(this.element.symbol);
  }
  private mousedown(event: Event) {
    event.preventDefault();
  }
}
</script>

<style scoped lang="stylus">
.element
  text-align center
  border 1px solid
  padding-top 10px
  padding-bottom 10px
  padding-left 1px
  padding-right 1px
  width 5.55%
  &:hover
    cursor pointer
  &:active
    color gray

.name
  font-size 0.7em

.weight
  font-size 0.6em

.symbol
  font-size 2.0em

.otherNonMetal
  background-color #DA70D6

.otherMainGroupElement
  background-color #B0C4DE

.alkaliMetal
  background-color #FFDEAD

.alkaliEarthMetal
  background-color #48D1CC

.transitionMetal
  background-color #F0E68C

.metalloid
  background-color #FFD700

.halogen
  background-color #90EE90

.nobleGas
  background-color #FFB6C1

.lanthanoid
  background-color #87CEFA

.actinoid
  background-color #F4A460

.syntheticAndRadioactive
  background-color #DCDCDC
</style>
