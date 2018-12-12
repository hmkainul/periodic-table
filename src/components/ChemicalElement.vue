<template>
  <div class="element" v-bind:id="symbol">
    <span class="number">{{ number }}<br></span>
    <span class="symbol">{{ symbol }}<br></span>
    <span class="name">{{ name }}<br></span>
    <span class="weight">{{ weight }}</span>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";

@Component
export default class HelloWorld extends Vue {
  @Prop() private number!: string;
  @Prop() private symbol!: string;
  @Prop() private name!: string;
  @Prop() private weight!: string;
}
</script>

<style scoped lang="stylus">
.element
  text-align center
  background-color #DA70D6
  border 1px solid
  padding-top 10px
  padding-bottom 10px
  padding-left 1px
  padding-right 1px
  width 5.55%
  &:hover
    cursor pointer
  &:active
    color: gray

.name
  font-size 0.7em

.weight
  font-size 0.6em

.symbol
  font-size 2.0em

</style>
